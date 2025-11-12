# VMC Chatbot Pro

Production-ready AI chatbot monorepo with intelligent orchestration, RAG retrieval, tool execution, and comprehensive guardrails.

[![CI/CD Pipeline](https://github.com/matiasportugau-ui/bmc-chatbot-pro/actions/workflows/ci.yml/badge.svg)](https://github.com/matiasportugau-ui/bmc-chatbot-pro/actions/workflows/ci.yml)

## 🏗️ Architecture

This is a **Turborepo monorepo** with TypeScript strict mode and comprehensive tracing via Langfuse.

```
vmc-chatbot-pro/
├── apps/
│   └── web/                    # Next.js 15 + React 19 + Vercel AI SDK
│       ├── app/
│       │   ├── api/chat/      # Edge API with SSE streaming
│       │   ├── page.tsx       # Main chat interface
│       │   └── layout.tsx     # Root layout
│       └── package.json
├── packages/
│   ├── core/                   # Orchestrator with intent routing
│   │   └── src/
│   │       ├── orchestrator.ts # Intent→RAG|Tool|LLM routing
│   │       └── index.ts
│   ├── tools/                  # Tool implementations
│   │   └── src/
│   │       ├── quote_bmc.ts   # BMC quote generation
│   │       └── index.ts
│   ├── rag/                    # Graph-based retrieval
│   │   └── src/
│   │       ├── graph.ts       # Vector DB + graph retrieval
│   │       └── index.ts
│   └── guardrails/            # Security & safety
│       └── src/
│           └── index.ts       # PII/injection/toxicity detection
├── .github/workflows/
│   └── ci.yml                 # CI/CD: lint→test→promptfoo→build→deploy
├── promptfoo.yaml             # AI evaluation (≥90% threshold)
├── vercel.json                # Vercel deployment config
├── docker-compose.yml         # Local dev + Vector DB
├── Dockerfile                 # Production container
├── .env.example               # Environment variables template
└── turbo.json                 # Turborepo pipeline config
```

## 🚀 Quick Start

### Prerequisites

- Node.js 18+ and npm 9+
- OpenAI API key
- Langfuse account (for tracing)

### Installation

```bash
# Clone the repository
git clone https://github.com/matiasportugau-ui/bmc-chatbot-pro.git
cd bmc-chatbot-pro

# Install dependencies
npm install

# Copy environment variables
cp .env.example .env
# Edit .env with your API keys

# Build all packages
npm run build

# Start development server
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) to see the chatbot interface.

## 📦 Packages

### 🧠 @vmc-chatbot-pro/core

Intelligent orchestration with intent classification and routing.

**Features:**

- Intent classification (RAG, TOOL, LLM, UNKNOWN)
- Request orchestration with Zod validation
- Langfuse tracing integration
- TypeScript strict mode

**Usage:**

```typescript
import { orchestrate, type OrchestratorRequest } from '@vmc-chatbot-pro/core';

const request: OrchestratorRequest = {
  messages: [{ role: 'user', content: 'Get a quote for BMC-500' }],
  userId: 'user-123',
  sessionId: 'session-456'
};

const response = await orchestrate(request);
console.log(response.intent); // 'TOOL'
```

### 🔧 @vmc-chatbot-pro/tools

Tool implementations for external integrations.

**Features:**

- BMC quote generation with Zod validation
- Extensible tool registration system
- Mock implementations for development

**Usage:**

```typescript
import { getQuoteBMC, type BMCQuoteRequest } from '@vmc-chatbot-pro/tools';

const quote = await getQuoteBMC({
  productId: 'BMC-500',
  quantity: 10,
  customerType: 'enterprise'
});
```

### 📚 @vmc-chatbot-pro/rag

Graph-based retrieval system for knowledge base queries.

**Features:**

- Vector database integration (Qdrant)
- Graph-based re-ranking
- Document chunking and metadata
- Configurable top-K retrieval

**Usage:**

```typescript
import { graphRetrieval } from '@vmc-chatbot-pro/rag';

const results = await graphRetrieval.retrieve({
  query: 'BMC API documentation',
  topK: 5,
  includeMetadata: true
});
```

### 🛡️ @vmc-chatbot-pro/guardrails

Security and safety layer for content filtering.

**Features:**

- **PII Detection:** Email, phone, SSN, credit cards
- **Injection Prevention:** SQL injection, prompt injection
- **Toxicity Filtering:** Harmful content detection
- Configurable thresholds
- Text sanitization

**Usage:**

```typescript
import { checkGuardrails } from '@vmc-chatbot-pro/guardrails';

const result = checkGuardrails('My email is test@example.com');
if (!result.passed) {
  console.log('Violations:', result.violations);
  console.log('Sanitized:', result.sanitizedText);
}
```

## 🌐 Web Application

Next.js 15 app with React 19 and Vercel AI SDK.

**Features:**

- Edge runtime for low latency
- Server-Sent Events (SSE) streaming
- Real-time chat interface
- Guardrails integration
- Intent-based routing

**API Endpoints:**

- `POST /api/chat` - Main chat endpoint with streaming

## 🔬 Testing & Quality

### Linting

```bash
npm run lint
```

### Type Checking

```bash
npm run typecheck
```

### Tests

```bash
npm run test
```

### AI Evaluation (Promptfoo)

```bash
# Install promptfoo
npm install -g promptfoo

# Run evaluation (must achieve ≥90% pass rate)
promptfoo eval
```

**Evaluation Areas:**

- Intent classification accuracy
- Guardrails effectiveness
- Response quality
- Tool execution correctness

## 🚢 Deployment

### Vercel (Recommended)

1. Install Vercel CLI:

```bash
npm i -g vercel
```

2. Deploy:

```bash
cd apps/web
vercel
```

3. Configure environment variables in Vercel dashboard

### Docker

```bash
# Build and run with docker-compose
docker-compose up -d

# Or build manually
docker build -t vmc-chatbot-pro .
docker run -p 3000:3000 --env-file .env vmc-chatbot-pro
```

## 🔧 Configuration

### Environment Variables

See `.env.example` for all available configuration options.

**Required:**

- `OPENAI_API_KEY` - OpenAI API key
- `LANGFUSE_PUBLIC_KEY` - Langfuse public key
- `LANGFUSE_SECRET_KEY` - Langfuse secret key

**Optional:**

- `BMC_API_KEY` - BMC API key for quote tool
- `VECTOR_DB_URL` - Vector database URL (default: http://localhost:6333)
- `ENABLE_PII_DETECTION` - Enable PII detection (default: true)
- `ENABLE_INJECTION_PREVENTION` - Enable injection prevention (default: true)
- `ENABLE_TOXICITY_FILTERING` - Enable toxicity filtering (default: true)

### Turborepo Configuration

Modify `turbo.json` to customize build pipelines and caching behavior.

## 📊 Monitoring & Tracing

All requests are automatically traced with **Langfuse**:

1. Sign up at [cloud.langfuse.com](https://cloud.langfuse.com)
2. Create a new project
3. Add credentials to `.env`
4. View traces in Langfuse dashboard

**Traced Operations:**

- Intent classification
- Orchestration decisions
- Tool executions
- RAG retrievals
- LLM generations

## 🔐 Security

### Guardrails

The system includes three layers of protection:

1. **PII Detection**
   - Regex-based pattern matching
   - Automatic redaction
   - Supports: email, phone, SSN, credit cards

2. **Injection Prevention**
   - SQL injection detection
   - Prompt injection detection
   - Obfuscation detection

3. **Toxicity Filtering**
   - Keyword-based detection
   - Configurable threshold
   - Severity levels: LOW, MEDIUM, HIGH, CRITICAL

### CI/CD Security

- CodeQL scanning (via `codeql_checker`)
- Dependency audits
- Promptfoo evaluation (≥90%)
- Automated security reviews

## 🛠️ Development

### Project Structure

```
# Workspace commands (run from root)
npm run dev        # Start all apps in dev mode
npm run build      # Build all packages
npm run lint       # Lint all packages
npm run test       # Test all packages
npm run clean      # Clean all build artifacts

# Package-specific commands (run from package directory)
cd packages/core
npm run build      # Build this package only
npm run dev        # Watch mode
npm run test       # Test this package
```

### Adding a New Package

1. Create package directory: `packages/new-package`
2. Add `package.json` with workspace reference
3. Add to `turbo.json` pipeline
4. Build and test

### Adding a New Tool

1. Create tool in `packages/tools/src/your-tool.ts`
2. Define Zod schemas for request/response
3. Implement tool function
4. Export from `packages/tools/src/index.ts`
5. Add tests

## 📝 Scripts Reference

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development servers |
| `npm run build` | Build all packages |
| `npm run lint` | Lint all code |
| `npm run typecheck` | Type check all packages |
| `npm run test` | Run all tests |
| `npm run clean` | Remove build artifacts |
| `npm run format` | Format code with Prettier |

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Run tests and linting
5. Submit a pull request

## 📄 License

MIT License - see LICENSE file for details

## 🙋 Support

- Documentation: [GitHub Wiki](https://github.com/matiasportugau-ui/bmc-chatbot-pro/wiki)
- Issues: [GitHub Issues](https://github.com/matiasportugau-ui/bmc-chatbot-pro/issues)

## 🎯 Roadmap

- [ ] Additional tool implementations
- [ ] Advanced RAG with hybrid search
- [ ] Multi-modal support
- [ ] Fine-tuned toxicity models
- [ ] Real-time analytics dashboard
- [ ] Multi-language support
