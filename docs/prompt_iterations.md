# Prompt Iteration Log - 100 Iterations

## Iteration 1 (v1) - Added Context & Structure
**Improvement**: Added project context and clearer structure
```
Create a production-ready chatbot monorepo called VMC-Chatbot-Pro that integrates open-source chatbot best practices. 
Context: This project integrates modules from matiasportugau-ui organization and follows patterns from Rasa, Botpress, LangChain, Haystack, and LlamaIndex.

Structure:
- packages/core/orchestrator.ts (intent router with RAG/Tool/LLM routing)
- packages/tools/ (reusable tool modules)
- packages/rag/graph.ts (retrieval-augmented generation graph)
- docs/ (research, reports, checklists)
- .github/workflows/ci.yml (lint, test, eval with Promptfoo)
- docker-compose.yml (PostgreSQL + Redis)
- vercel.json (Edge deployment config)
- promptfoo.yaml (evaluation suite)

Tech stack: Node.js 20, TypeScript, Next.js 15, React 19, Drizzle ORM, PostgreSQL (Neon), Redis optional.
Dependencies: typescript, ts-node, @types/node, promptfoo, drizzle-orm, @vercel/ai-sdk.
```

## Iteration 2 (v2) - Added Examples & Format Specs
**Improvement**: Included concrete examples and output format
```
Create VMC-Chatbot-Pro: A production-ready chatbot monorepo integrating matiasportugau-ui modules with open-source best practices (Rasa, Botpress, LangChain patterns).

REQUIREMENTS:
1. Monorepo structure with TypeScript
2. Core orchestrator with intent routing (RAG | Tool | LLM)
3. RAG implementation with vector store
4. CI/CD pipeline with quality gates
5. Multi-channel support ready

FILE STRUCTURE (create these):
packages/
  core/
    orchestrator.ts  // Example: class Orchestrator { async route(intent) { ... } }
  tools/
    index.ts  // Tool registry
  rag/
    graph.ts  // Example: class RAGGraph { async retrieveAndGenerate(query) { ... } }
docs/
  research_v1.md  // Placeholder: "Research on open-source chatbots"
  matriz_repos.csv  // Placeholder: "Repo,Language,Tests,Modularity"
.github/workflows/
  ci.yml  // Example: runs lint, test, promptfoo eval
docker-compose.yml  // PostgreSQL + Redis services
vercel.json  // Edge function config
promptfoo.yaml  // Evaluation config with test cases

TECH STACK: Node.js 20, TypeScript, Next.js 15, React 19, Drizzle ORM, PostgreSQL, Redis.
INSTALL: npm install typescript ts-node @types/node promptfoo drizzle-orm @vercel/ai-sdk next@15 react@19
```

## Iteration 3 (v3) - Added Delimiters & Style
**Improvement**: Used delimiters and specified code style
```
=== PROJECT: VMC-Chatbot-Pro ===
A production-ready chatbot monorepo integrating matiasportugau-ui modules.

=== CONTEXT ===
Integrates: ChatBOT, background-agents, Dashboard-bmc from matiasportugau-ui.
Follows patterns from: Rasa (pipeline-based), Botpress (plugin system), LangChain (composable components).

=== STRUCTURE ===
packages/
  core/
    orchestrator.ts  // Intent router: Router(intent) → RAG | Tool | LLM
  tools/
    index.ts  // Tool registry with Zod schemas
  rag/
    graph.ts  // RAG graph: embed → retrieve → generate
docs/
  research_v1.md
  matriz_repos.csv
  security_report.md
.github/workflows/
  ci.yml  // Steps: lint → test → promptfoo eval → build
docker-compose.yml  // Services: app, postgres, redis
vercel.json
promptfoo.yaml

=== CODE STYLE ===
- TypeScript strict mode
- ESLint + Prettier
- Async/await (no callbacks)
- Zod for validation
- Error handling with try/catch

=== DEPENDENCIES ===
npm install typescript@latest ts-node @types/node promptfoo drizzle-orm @vercel/ai-sdk next@15 react@19 zod
```

## Iteration 4 (v4) - Removed Ambiguities
**Improvement**: Clarified ambiguous terms, added specific versions
```
=== PROJECT: VMC-Chatbot-Pro ===
Production-ready chatbot monorepo for matiasportugau-ui organization.

=== CONTEXT ===
Purpose: Integrate existing repos (ChatBOT, background-agents, Dashboard-bmc) into unified chatbot.
Architecture patterns: Pipeline-based (Rasa), plugin system (Botpress), composable components (LangChain).

=== FILE STRUCTURE (EXACT PATHS) ===
packages/
  core/
    orchestrator.ts  // Main class: Orchestrator with method handleRequest(input: string): Promise<string>
  tools/
    index.ts  // Export all tools
  rag/
    graph.ts  // Class: RAGGraph with method retrieveAndGenerate(query: string): Promise<string>
docs/
  research_v1.md  // Content: "Research on 5 open-source chatbot projects"
  matriz_repos.csv  // Columns: Repo,Language,Tests,Modularity,Last Activity,License
  security_report.md  // Placeholder: "Security audit results"
.github/workflows/
  ci.yml  // GitHub Actions workflow: runs on push/PR, uses Node 20, executes: npm ci → lint → test → promptfoo eval
docker-compose.yml  // Version 3, services: app (build: .), postgres (image: postgres:15), redis (image: redis:7)
vercel.json  // Version 2, builds from packages/core/orchestrator.ts
promptfoo.yaml  // Config with prompts array, providers (openai), tests array

=== TECHNICAL SPECIFICATIONS ===
Node.js: 20.x
TypeScript: 5.x (strict mode enabled)
Next.js: 15.0.0
React: 19.0.0
PostgreSQL: 15 (via Neon or Docker)
Redis: 7 (optional, for caching)

=== DEPENDENCIES (EXACT VERSIONS) ===
npm install --save-dev typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo@latest
npm install --save drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 react-dom@19.0.0 zod@3.22.4

=== CODE REQUIREMENTS ===
- All TypeScript files use strict mode
- All async functions use async/await (no .then())
- All inputs validated with Zod schemas
- All errors caught and logged
- All exports use named exports (no default exports for classes)
```

## Iteration 5 (v5) - Added KPIs & Quality Gates
**Improvement**: Included quality metrics and SLOs
```
=== PROJECT: VMC-Chatbot-Pro ===
Production-ready chatbot monorepo with quality gates and observability.

=== CONTEXT ===
Goal: Integrate matiasportugau-ui repos (ChatBOT, background-agents, Dashboard-bmc) into unified chatbot.
Quality targets: ≥90% eval pass rate, p95 latency ≤2.5s, RAG hallucination rate ≤5%.

=== FILE STRUCTURE ===
packages/core/orchestrator.ts  // Orchestrator class with timeout/retry logic
packages/tools/index.ts  // Tool registry with Zod validation
packages/rag/graph.ts  // RAGGraph with provenance validation
docs/research_v1.md  // Research findings
docs/matriz_repos.csv  // Repo analysis matrix
.github/workflows/ci.yml  // CI with quality gates (must pass lint, test, evals ≥90%)
docker-compose.yml  // Full stack: app, postgres, redis
vercel.json  // Edge deployment
promptfoo.yaml  // Eval config targeting ≥90% pass rate

=== QUALITY REQUIREMENTS ===
- TypeScript strict mode
- 100% test coverage for core modules
- Promptfoo evals must pass ≥90%
- ESLint with zero errors
- All async operations have timeout (default 5s)
- All external calls have retry logic (max 3 attempts)

=== DEPENDENCIES ===
npm install typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo@latest drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 zod@3.22.4
```

## Iteration 6 (v6) - Added Observability & Guardrails
**Improvement**: Included observability and safety requirements
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with observability, guardrails, and multi-channel support.

=== CONTEXT ===
Integrates: ChatBOT (core logic), background-agents (agent framework), Dashboard-bmc (dashboard).
Includes: Observability (Langfuse + OpenTelemetry), Guardrails (PII detection, toxicity filtering), Multi-channel (web, mobile).

=== FILE STRUCTURE ===
packages/core/orchestrator.ts  // With Langfuse tracing and guardrail checks
packages/tools/index.ts  // Tools with observability hooks
packages/rag/graph.ts  // With provenance validation and cost tracking
packages/guardrails/  // PII, toxicity, injection detection
packages/observability/  // Langfuse integration, OpenTelemetry spans
docs/research_v1.md
docs/matriz_repos.csv
.github/workflows/ci.yml  // Includes security scan, dependency audit
docker-compose.yml  // With langfuse service
vercel.json
promptfoo.yaml

=== OBSERVABILITY REQUIREMENTS ===
- All LLM calls logged to Langfuse with cost tracking
- OpenTelemetry spans for all async operations
- Error tracking with stack traces
- Latency metrics (p50, p95, p99)

=== GUARDRAILS REQUIREMENTS ===
- PII detection before LLM calls
- Toxicity filtering on user input
- Prompt injection detection
- Output validation with Zod

=== DEPENDENCIES ===
npm install typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo@latest drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 zod@3.22.4 langfuse@latest @langfuse/opentelemetry
```

## Iteration 7 (v7) - Added Specific Code Examples
**Improvement**: Included concrete code snippets as examples
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot monorepo with complete implementation examples.

=== CONTEXT ===
Integrates matiasportugau-ui modules following Rasa/Botpress/LangChain patterns.

=== CODE EXAMPLES (IMPLEMENT THESE PATTERNS) ===

Example 1 - orchestrator.ts:
```typescript
import { z } from 'zod';
import { RAGGraph } from '../rag/graph';
import { ToolRegistry } from '../tools';

class Orchestrator {
  async handleRequest(input: string): Promise<string> {
    const intent = await this.detectIntent(input);
    if (intent === 'rag') return await this.ragGraph.retrieveAndGenerate(input);
    if (intent === 'tool') return await this.tools.execute(input);
    return await this.llm.generate(input);
  }
}
```

Example 2 - rag/graph.ts:
```typescript
class RAGGraph {
  async retrieveAndGenerate(query: string): Promise<string> {
    const embedding = await this.embeddings.embed(query);
    const docs = await this.vectorStore.retrieve(embedding, { topK: 5 });
    return await this.llm.generate(docs, query);
  }
}
```

=== FILE STRUCTURE ===
[Same as v6]

=== DEPENDENCIES ===
[Same as v6]
```

## Iteration 8 (v8) - Added Error Handling Patterns
**Improvement**: Specified error handling requirements
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with comprehensive error handling.

=== ERROR HANDLING REQUIREMENTS ===
- All async functions wrapped in try/catch
- Timeout errors: throw TimeoutError (custom class)
- Retry logic: exponential backoff (1s, 2s, 4s)
- Error logging: structured logs with context
- User-facing errors: sanitized (no stack traces)

Example error handling:
```typescript
async handleRequest(input: string): Promise<string> {
  try {
    return await this.processWithTimeout(input, 5000);
  } catch (error) {
    this.logger.error('Request failed', { input, error });
    throw new UserFacingError('Sorry, something went wrong');
  }
}
```

=== FILE STRUCTURE ===
[Same as v7]

=== DEPENDENCIES ===
[Same as v7]
```

## Iteration 9 (v9) - Added Testing Requirements
**Improvement**: Included testing specifications
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with comprehensive testing.

=== TESTING REQUIREMENTS ===
- Unit tests: Jest or Vitest, ≥80% coverage
- Integration tests: Test full orchestrator flow
- E2E tests: Test complete user journey
- Promptfoo evals: ≥90% pass rate required

Test file structure:
packages/core/__tests__/orchestrator.test.ts
packages/rag/__tests__/graph.test.ts
e2e/tests/chatbot-flow.test.ts

Example test:
```typescript
describe('Orchestrator', () => {
  it('should route to RAG for knowledge queries', async () => {
    const result = await orchestrator.handleRequest('What is VMC?');
    expect(result).toContain('chatbot');
  });
});
```

=== FILE STRUCTURE ===
[Same as v8]

=== DEPENDENCIES ===
npm install --save-dev jest@29.7.0 @types/jest@29.5.11 vitest@1.0.0
[Same as v8 for production deps]
```

## Iteration 10 (v10) - Added Deployment Config Details
**Improvement**: Specified exact deployment configurations
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with complete deployment configs.

=== DEPLOYMENT CONFIGS ===

docker-compose.yml:
```yaml
version: '3.8'
services:
  app:
    build: .
    ports: ["3000:3000"]
    environment:
      DATABASE_URL: postgresql://user:pass@db:5432/vmc
      REDIS_URL: redis://redis:6379
  db:
    image: postgres:15
    environment:
      POSTGRES_DB: vmc
      POSTGRES_PASSWORD: ${DB_PASSWORD}
  redis:
    image: redis:7-alpine
```

vercel.json:
```json
{
  "version": 2,
  "builds": [{"src": "packages/core/orchestrator.ts", "use": "@vercel/node"}],
  "routes": [{"src": "/api/chat", "dest": "packages/core/orchestrator.ts"}],
  "env": {
    "OPENAI_API_KEY": "@openai-key",
    "LANGFUSE_SECRET_KEY": "@langfuse-key"
  }
}
```

=== FILE STRUCTURE ===
[Same as v9]

=== DEPENDENCIES ===
[Same as v9]
```

## Iteration 11 (v11) - Added Documentation Requirements
**Improvement**: Specified documentation standards
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with comprehensive documentation.

=== DOCUMENTATION REQUIREMENTS ===
- All public functions have JSDoc comments
- README.md includes setup instructions
- Architecture diagram in docs/arquitectura_v1.png (placeholder)
- API documentation for all endpoints
- Contributing guide (CONTRIBUTING.md)

Example JSDoc:
```typescript
/**
 * Routes user input to appropriate handler (RAG, Tool, or LLM)
 * @param input - User query string
 * @returns Promise resolving to chatbot response
 * @throws {TimeoutError} If request exceeds 5s timeout
 */
async handleRequest(input: string): Promise<string>
```

=== FILE STRUCTURE ===
[Same as v10]

=== DEPENDENCIES ===
[Same as v10]
```

## Iteration 12 (v12) - Added Security Requirements
**Improvement**: Included security best practices
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with security hardening.

=== SECURITY REQUIREMENTS ===
- All secrets in environment variables (never hardcoded)
- Input sanitization for all user inputs
- Rate limiting: 100 requests/minute per IP
- CORS configured for specific origins
- Dependency audit: npm audit (zero high/critical vulnerabilities)
- Secret scanning: GitHub Dependabot enabled

Security checklist:
- [ ] .env.example file (no secrets)
- [ ] .gitignore includes .env
- [ ] API keys rotated regularly
- [ ] HTTPS only in production
- [ ] Input validation with Zod schemas

=== FILE STRUCTURE ===
[Same as v11]

=== DEPENDENCIES ===
[Same as v11]
```

## Iteration 13 (v13) - Added Performance Requirements
**Improvement**: Specified performance targets
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot optimized for performance.

=== PERFORMANCE REQUIREMENTS ===
- Latency p95: ≤2.5s (first token), ≤6s (complete response)
- Caching: Redis for frequent queries (TTL: 5min)
- Connection pooling: PostgreSQL (max 20 connections)
- Streaming: SSE for real-time responses
- Bundle size: <500KB (gzipped)

Performance optimizations:
- Lazy loading for heavy modules
- Debouncing for user input
- Request batching where possible
- CDN for static assets

=== FILE STRUCTURE ===
[Same as v12]

=== DEPENDENCIES ===
[Same as v12]
```

## Iteration 14 (v14) - Added Multi-Channel Support
**Improvement**: Specified multi-channel architecture
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with multi-channel support.

=== MULTI-CHANNEL REQUIREMENTS ===
- Web: Next.js 15 with React 19, SSE streaming
- Mobile: REST API compatible with mobile apps
- Future: Slack, WhatsApp, Telegram integrations

Channel abstraction:
```typescript
interface ChannelAdapter {
  send(message: string): Promise<void>;
  receive(): Promise<string>;
}

class WebChannel implements ChannelAdapter { ... }
class MobileChannel implements ChannelAdapter { ... }
```

=== FILE STRUCTURE ===
packages/channels/
  web.ts
  mobile.ts
  index.ts
[Rest same as v13]

=== DEPENDENCIES ===
[Same as v13]
```

## Iteration 15 (v15) - Added Monitoring & Alerts
**Improvement**: Included monitoring setup
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with monitoring and alerting.

=== MONITORING REQUIREMENTS ===
- Langfuse dashboard: Track all LLM calls, costs, latency
- OpenTelemetry: Distributed tracing
- Error tracking: Sentry or similar
- Uptime monitoring: Health check endpoint /health
- Alerting: PagerDuty or Slack webhooks for critical errors

Monitoring endpoints:
- GET /health → { status: "ok", timestamp: "..." }
- GET /metrics → Prometheus format
- GET /traces → OpenTelemetry traces

=== FILE STRUCTURE ===
packages/monitoring/
  health.ts
  metrics.ts
  alerts.ts
[Rest same as v14]

=== DEPENDENCIES ===
npm install @sentry/nextjs@latest @opentelemetry/api@latest
[Same as v14]
```

## Iteration 16 (v16) - Added Database Schema
**Improvement**: Specified database requirements
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with database schema.

=== DATABASE REQUIREMENTS ===
- ORM: Drizzle ORM
- Database: PostgreSQL 15 (Neon or self-hosted)
- Schema: Conversations, Messages, UserSessions tables

Example schema (Drizzle):
```typescript
import { pgTable, text, timestamp } from 'drizzle-orm/pg-core';

export const conversations = pgTable('conversations', {
  id: text('id').primaryKey(),
  userId: text('user_id').notNull(),
  createdAt: timestamp('created_at').defaultNow(),
});
```

=== FILE STRUCTURE ===
packages/db/
  schema.ts
  migrations/
[Rest same as v15]

=== DEPENDENCIES ===
npm install drizzle-orm@0.29.0 drizzle-kit@0.20.0 @neondatabase/serverless@latest
[Same as v15]
```

## Iteration 17 (v17) - Added CI/CD Pipeline Details
**Improvement**: Specified complete CI/CD workflow
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with complete CI/CD pipeline.

=== CI/CD PIPELINE ===
.github/workflows/ci.yml must include:
1. Lint: ESLint with zero errors
2. Type check: tsc --noEmit
3. Test: npm test (coverage ≥80%)
4. Eval: promptfoo eval (pass rate ≥90%)
5. Build: npm run build (must succeed)
6. Security: npm audit, secret scanning
7. Deploy: Vercel preview (on PR) or production (on main)

Pipeline gates:
- All steps must pass
- No merge if evals <90%
- No deploy if security issues found

=== FILE STRUCTURE ===
[Same as v16]

=== DEPENDENCIES ===
[Same as v16]
```

## Iteration 18 (v18) - Added Environment Configuration
**Improvement**: Specified environment setup
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with environment configuration.

=== ENVIRONMENT SETUP ===
Required .env variables:
- DATABASE_URL (PostgreSQL connection string)
- REDIS_URL (optional, for caching)
- OPENAI_API_KEY (or LITELLM_API_KEY for failover)
- LANGFUSE_SECRET_KEY (for observability)
- NODE_ENV (development | staging | production)

.env.example template:
```
DATABASE_URL=postgresql://user:pass@localhost:5432/vmc
REDIS_URL=redis://localhost:6379
OPENAI_API_KEY=sk-...
LANGFUSE_SECRET_KEY=sk-...
NODE_ENV=development
```

=== FILE STRUCTURE ===
.env.example
.env (gitignored)
[Rest same as v17]

=== DEPENDENCIES ===
npm install dotenv@16.3.1
[Same as v17]
```

## Iteration 19 (v19) - Added Rollback Strategy
**Improvement**: Included deployment rollback procedures
```
=== PROJECT: VMC-Chatbot-Pro ===
Production chatbot with rollback strategy.

=== ROLLBACK REQUIREMENTS ===
- Automatic rollback if KPIs not met post-deploy
- Health check after deploy: /health endpoint
- KPI monitoring: Latency, error rate, eval pass rate
- Rollback trigger: If p95 latency >6s OR error rate >5% OR evals <90%

Rollback process:
1. Monitor metrics for 5 minutes post-deploy
2. If KPIs fail → automatic rollback to previous version
3. Alert team via Slack/PagerDuty
4. Log rollback reason in Langfuse

=== FILE STRUCTURE ===
packages/deployment/
  rollback.ts
  health-check.ts
[Rest same as v18]

=== DEPENDENCIES ===
[Same as v18]
```

## Iteration 20 (v20) - Final Optimized Prompt
**Improvement**: Consolidated all improvements into final version
```
=== PROJECT: VMC-Chatbot-Pro ===
Production-ready chatbot monorepo integrating matiasportugau-ui modules with complete observability, guardrails, testing, and deployment.

=== CONTEXT ===
Purpose: Integrate ChatBOT, background-agents, Dashboard-bmc from matiasportugau-ui into unified production chatbot.
Architecture: Follows Rasa (pipeline), Botpress (plugins), LangChain (composable), Haystack (RAG), LlamaIndex (data framework) patterns.
Quality targets: ≥90% eval pass, p95 latency ≤2.5s, RAG hallucination ≤5%, CI error rate <5%.

=== FILE STRUCTURE (CREATE EXACT PATHS) ===
packages/
  core/
    orchestrator.ts  // Intent router: Router(intent) → RAG | Tool | LLM with timeout/retry
  tools/
    index.ts  // Tool registry with Zod validation
  rag/
    graph.ts  // RAGGraph: embed → retrieve → generate with provenance validation
  guardrails/
    pii-detector.ts  // PII detection before LLM calls
    toxicity-filter.ts  // Toxicity filtering on input
  observability/
    langfuse.ts  // Langfuse integration with cost tracking
    opentelemetry.ts  // OpenTelemetry spans
  channels/
    web.ts  // Web channel adapter (Next.js 15 + React 19)
    mobile.ts  // Mobile REST API adapter
  monitoring/
    health.ts  // GET /health endpoint
    metrics.ts  // Prometheus metrics
  db/
    schema.ts  // Drizzle schema: conversations, messages, user_sessions
    migrations/  // Database migrations
docs/
  research_v1.md  // "Research on 5 open-source chatbot projects"
  matriz_repos.csv  // "Repo,Language,Tests,Modularity,Last Activity,License"
  security_report.md  // Security audit results
  post_deploy_checklist.md  // Deployment verification steps
  readiness_report.md  // Production readiness assessment
.github/workflows/
  ci.yml  // Lint → Type check → Test (≥80% coverage) → Eval (≥90% pass) → Build → Security scan → Deploy
docker-compose.yml  // Services: app, postgres:15, redis:7-alpine
vercel.json  // Edge deployment with env vars
promptfoo.yaml  // Evaluation config targeting ≥90% pass rate
.env.example  // Template with all required env vars (no secrets)

=== CODE EXAMPLES ===
orchestrator.ts:
```typescript
import { z } from 'zod';
import { RAGGraph } from '../rag/graph';
import { ToolRegistry } from '../tools';
import { Langfuse } from '../observability/langfuse';

export class Orchestrator {
  async handleRequest(input: string): Promise<string> {
    const trace = Langfuse.trace({ input });
    try {
      const intent = await this.detectIntent(input);
      let result: string;
      if (intent === 'rag') result = await this.ragGraph.retrieveAndGenerate(input);
      else if (intent === 'tool') result = await this.tools.execute(input);
      else result = await this.llm.generate(input);
      trace.end({ output: result });
      return result;
    } catch (error) {
      trace.end({ error: error.message });
      throw new UserFacingError('Sorry, something went wrong');
    }
  }
}
```

=== TECHNICAL SPECS ===
Node.js: 20.x | TypeScript: 5.x (strict) | Next.js: 15.0.0 | React: 19.0.0 | PostgreSQL: 15 | Redis: 7

=== DEPENDENCIES ===
npm install --save-dev typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo@latest jest@29.7.0 vitest@1.0.0
npm install --save drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 zod@3.22.4 langfuse@latest @opentelemetry/api@latest dotenv@16.3.1

=== QUALITY GATES ===
- TypeScript strict mode, ESLint zero errors
- Test coverage ≥80%, Promptfoo evals ≥90%
- All async ops: timeout 5s, retry max 3 attempts
- All inputs: Zod validation
- All errors: try/catch with structured logging
```

## Iterations 21-30: Refinements
**Focus**: Clarity, specificity, removing redundancy

## Iteration 21 (v21) - Removed Redundancy
**Improvement**: Eliminated duplicate information, streamlined structure
```
=== VMC-Chatbot-Pro: Production Chatbot Monorepo ===

CONTEXT: Integrate matiasportugau-ui repos (ChatBOT, background-agents, Dashboard-bmc) following Rasa/Botpress/LangChain patterns.

STRUCTURE:
packages/core/orchestrator.ts  // Intent router with timeout/retry
packages/tools/index.ts  // Tool registry (Zod schemas)
packages/rag/graph.ts  // RAG with provenance validation
packages/guardrails/  // PII, toxicity, injection detection
packages/observability/  // Langfuse + OpenTelemetry
packages/channels/  // Web (Next.js 15), Mobile (REST API)
packages/monitoring/  // Health, metrics endpoints
packages/db/  // Drizzle schema + migrations
docs/  // Research, security reports, checklists
.github/workflows/ci.yml  // Quality gates: lint→test→eval→build→deploy
docker-compose.yml  // postgres:15, redis:7
vercel.json  // Edge config
promptfoo.yaml  // Eval suite (≥90% target)
.env.example  // Env template

TECH: Node 20, TS 5 (strict), Next.js 15, React 19, Drizzle, PostgreSQL 15, Redis 7

DEPS: typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo jest vitest drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 zod@3.22.4 langfuse @opentelemetry/api dotenv@16.3.1

QUALITY: TS strict, ESLint zero errors, tests ≥80% coverage, evals ≥90%, timeouts 5s, retries 3x, Zod validation, structured logging.
```

## Iteration 22 (v22) - Added Priority Order
**Improvement**: Specified implementation priority
```
=== VMC-Chatbot-Pro ===

PRIORITY 1 (MVP):
- packages/core/orchestrator.ts (basic intent routing)
- packages/rag/graph.ts (basic RAG)
- .github/workflows/ci.yml (basic CI)
- promptfoo.yaml (basic evals)

PRIORITY 2 (Production):
- packages/guardrails/ (PII, toxicity)
- packages/observability/ (Langfuse, OpenTelemetry)
- packages/monitoring/ (health, metrics)

PRIORITY 3 (Scale):
- packages/channels/ (multi-channel)
- packages/db/ (persistence)
- docker-compose.yml (full stack)

[Rest same as v21]
```

## Iteration 23 (v23) - Added Constraints
**Improvement**: Specified what NOT to do
```
=== VMC-Chatbot-Pro ===

DO:
- Use TypeScript strict mode
- Validate all inputs with Zod
- Log all errors with context
- Use async/await (no callbacks)

DON'T:
- Hardcode secrets (use env vars)
- Use default exports for classes
- Skip error handling
- Expose stack traces to users

[Rest same as v22]
```

## Iteration 24 (v24) - Added Naming Conventions
**Improvement**: Specified naming standards
```
=== VMC-Chatbot-Pro ===

NAMING:
- Files: kebab-case (orchestrator.ts, rag-graph.ts)
- Classes: PascalCase (Orchestrator, RAGGraph)
- Functions: camelCase (handleRequest, retrieveAndGenerate)
- Constants: UPPER_SNAKE_CASE (MAX_RETRIES = 3)
- Interfaces: PascalCase with 'I' prefix optional (IChannelAdapter)

[Rest same as v23]
```

## Iteration 25 (v25) - Added File Templates
**Improvement**: Provided exact file content templates
```
=== VMC-Chatbot-Pro ===

TEMPLATE: orchestrator.ts
```typescript
import { z } from 'zod';
import { RAGGraph } from '../rag/graph';
import { ToolRegistry } from '../tools';

const InputSchema = z.object({ query: z.string().min(1) });

export class Orchestrator {
  constructor(
    private ragGraph: RAGGraph,
    private tools: ToolRegistry
  ) {}

  async handleRequest(input: string): Promise<string> {
    const validated = InputSchema.parse({ query: input });
    // Implementation here
  }
}
```

[Rest same as v24]
```

## Iteration 26 (v26) - Added Integration Points
**Improvement**: Specified how modules connect
```
=== VMC-Chatbot-Pro ===

INTEGRATION:
- Orchestrator imports RAGGraph, ToolRegistry
- RAGGraph uses embeddings + vector store + LLM
- Tools register with Zod schemas
- All modules log to Langfuse via observability package
- Channels call Orchestrator.handleRequest()

[Rest same as v25]
```

## Iteration 27 (v27) - Added Validation Rules
**Improvement**: Specified validation requirements
```
=== VMC-Chatbot-Pro ===

VALIDATION:
- User input: Zod schema, max length 1000 chars
- API responses: Zod schema validation
- Database queries: Parameterized (prevent SQL injection)
- Environment vars: Validated on startup (missing vars = error)

[Rest same as v26]
```

## Iteration 28 (v28) - Added Logging Standards
**Improvement**: Specified logging requirements
```
=== VMC-Chatbot-Pro ===

LOGGING:
- Format: Structured JSON logs
- Levels: error, warn, info, debug
- Context: Include requestId, userId, timestamp
- Sensitive data: Never log PII, API keys, passwords
- Destination: Console (dev), Langfuse (prod)

[Rest same as v27]
```

## Iteration 29 (v29) - Added API Contract
**Improvement**: Specified API interface
```
=== VMC-Chatbot-Pro ===

API CONTRACT:
POST /api/chat
Request: { query: string, userId?: string, sessionId?: string }
Response: { response: string, sessionId: string, latency: number }
Errors: 400 (validation), 429 (rate limit), 500 (server error)

GET /health
Response: { status: "ok" | "degraded", timestamp: string, checks: {...} }

[Rest same as v28]
```

## Iteration 30 (v30) - Added Configuration Management
**Improvement**: Specified config approach
```
=== VMC-Chatbot-Pro ===

CONFIG:
- Environment: .env files (dev), Vercel env vars (prod)
- Feature flags: Environment-based (FEATURE_RAG_ENABLED=true)
- Secrets: Never commit, use Vercel secrets or .env.local
- Validation: Validate all config on app startup

[Rest same as v29]
```

## Iterations 31-40: Advanced Features

## Iteration 31 (v31) - Added Caching Strategy
**Improvement**: Specified caching requirements
```
=== VMC-Chatbot-Pro ===

CACHING:
- Redis: Cache frequent queries (TTL: 5min)
- Cache key: hash(query + userId)
- Cache invalidation: On new data ingestion
- Fallback: If Redis down, proceed without cache (degraded mode)

[Rest same as v30]
```

## Iteration 32 (v32) - Added Rate Limiting
**Improvement**: Specified rate limiting
```
=== VMC-Chatbot-Pro ===

RATE LIMITING:
- Per IP: 100 requests/minute
- Per user: 1000 requests/hour (if authenticated)
- Implementation: Express rate-limit or similar
- Response: 429 with Retry-After header

[Rest same as v31]
```

## Iteration 33 (v33) - Added Streaming Support
**Improvement**: Specified SSE streaming
```
=== VMC-Chatbot-Pro ===

STREAMING:
- Use @vercel/ai-sdk for SSE streaming
- Stream tokens as they're generated (not wait for full response)
- Client: Use useChat hook from @vercel/ai-sdk
- Fallback: If streaming fails, return full response

[Rest same as v32]
```

## Iteration 34 (v34) - Added Session Management
**Improvement**: Specified session handling
```
=== VMC-Chatbot-Pro ===

SESSIONS:
- Store in PostgreSQL (conversations table)
- Session ID: UUID v4
- TTL: 24 hours of inactivity
- Context: Maintain conversation history in session

[Rest same as v33]
```

## Iteration 35 (v35) - Added Cost Tracking
**Improvement**: Specified cost monitoring
```
=== VMC-Chatbot-Pro ===

COST TRACKING:
- Log all LLM calls to Langfuse with token counts
- Track cost per request (model-specific pricing)
- Alert if daily cost exceeds threshold
- Dashboard: Show cost trends in Langfuse

[Rest same as v34]
```

## Iteration 36 (v36) - Added A/B Testing Support
**Improvement**: Specified experimentation
```
=== VMC-Chatbot-Pro ===

A/B TESTING:
- Feature flags for prompt variations
- Track performance metrics per variant
- Langfuse: Tag traces with experiment ID
- Analysis: Compare eval pass rates, latency, cost

[Rest same as v35]
```

## Iteration 37 (v37) - Added Backup Strategy
**Improvement**: Specified backup requirements
```
=== VMC-Chatbot-Pro ===

BACKUPS:
- Database: Daily automated backups (PostgreSQL)
- Retention: 30 days
- Restore: Test restore procedure quarterly
- Version control: All code in Git (backup via GitHub)

[Rest same as v36]
```

## Iteration 38 (v38) - Added Disaster Recovery
**Improvement**: Specified DR plan
```
=== VMC-Chatbot-Pro ===

DISASTER RECOVERY:
- RTO: 1 hour (Recovery Time Objective)
- RPO: 24 hours (Recovery Point Objective)
- Failover: Vercel automatic failover to backup region
- Database: Neon automatic backups + point-in-time recovery

[Rest same as v37]
```

## Iteration 39 (v39) - Added Compliance
**Improvement**: Specified compliance requirements
```
=== VMC-Chatbot-Pro ===

COMPLIANCE:
- GDPR: PII detection and anonymization
- Data retention: User data deleted after 90 days of inactivity
- Audit logs: All actions logged (who, what, when)
- Privacy policy: Document data usage in README

[Rest same as v38]
```

## Iteration 40 (v40) - Added Accessibility
**Improvement**: Specified a11y requirements
```
=== VMC-Chatbot-Pro ===

ACCESSIBILITY:
- WCAG 2.1 AA compliance
- Keyboard navigation support
- Screen reader compatible
- ARIA labels on all interactive elements
- Color contrast: ≥4.5:1 ratio

[Rest same as v39]
```

## Iterations 41-50: Optimization

## Iteration 41 (v41) - Added Bundle Optimization
**Improvement**: Specified bundle size targets
```
=== VMC-Chatbot-Pro ===

BUNDLE OPTIMIZATION:
- Target: <500KB gzipped for initial load
- Code splitting: Lazy load RAG, tools modules
- Tree shaking: Remove unused code
- Compression: Gzip + Brotli
- CDN: Static assets via Vercel CDN

[Rest same as v40]
```

## Iteration 42 (v42) - Added Database Optimization
**Improvement**: Specified DB performance
```
=== VMC-Chatbot-Pro ===

DATABASE OPTIMIZATION:
- Indexes: On userId, sessionId, createdAt columns
- Connection pooling: Max 20 connections
- Query optimization: Use EXPLAIN ANALYZE
- Read replicas: For read-heavy workloads (future)

[Rest same as v41]
```

## Iteration 43 (v43) - Added Memory Management
**Improvement**: Specified memory constraints
```
=== VMC-Chatbot-Pro ===

MEMORY:
- Max heap: 512MB (Node.js --max-old-space-size)
- Memory monitoring: Alert if >80% usage
- Garbage collection: Monitor GC pauses
- Leak detection: Use clinic.js or similar

[Rest same as v42]
```

## Iteration 44 (v44) - Added Load Testing
**Improvement**: Specified load testing
```
=== VMC-Chatbot-Pro ===

LOAD TESTING:
- Tool: k6 or Artillery
- Scenarios: 100 concurrent users, ramp-up 10s
- Targets: p95 latency <6s under load
- Run: Before each major release

[Rest same as v43]
```

## Iteration 45 (v45) - Added Dependency Management
**Improvement**: Specified dependency strategy
```
=== VMC-Chatbot-Pro ===

DEPENDENCIES:
- Lock file: package-lock.json (commit to Git)
- Updates: Dependabot for automated PRs
- Security: npm audit weekly, fix high/critical
- Pinning: Pin exact versions for production deps

[Rest same as v44]
```

## Iteration 46 (v46) - Added Documentation Standards
**Improvement**: Specified doc requirements
```
=== VMC-Chatbot-Pro ===

DOCUMENTATION:
- README: Setup, architecture, deployment
- API docs: OpenAPI/Swagger spec
- Code comments: JSDoc for all public functions
- Architecture: Mermaid diagrams in docs/
- Changelog: Keep CHANGELOG.md updated

[Rest same as v45]
```

## Iteration 47 (v47) - Added Onboarding
**Improvement**: Specified developer onboarding
```
=== VMC-Chatbot-Pro ===

ONBOARDING:
- Quickstart: README with 5-minute setup
- Development: docker-compose up for local stack
- Testing: npm test for test suite
- Contributing: CONTRIBUTING.md with guidelines

[Rest same as v46]
```

## Iteration 48 (v48) - Added Code Review Process
**Improvement**: Specified review requirements
```
=== VMC-Chatbot-Pro ===

CODE REVIEW:
- Minimum: 2 approvals for main branch
- Checklist: Tests pass, no lint errors, docs updated
- Automated: CI must pass before merge
- Manual: Review security-sensitive code

[Rest same as v47]
```

## Iteration 49 (v49) - Added Release Process
**Improvement**: Specified release workflow
```
=== VMC-Chatbot-Pro ===

RELEASE:
- Versioning: Semantic versioning (MAJOR.MINOR.PATCH)
- Changelog: Update before release
- Testing: Full test suite + manual smoke tests
- Deployment: Staging first, then production
- Rollback: Automated if KPIs fail

[Rest same as v48]
```

## Iteration 50 (v50) - Added Metrics Dashboard
**Improvement**: Specified monitoring dashboard
```
=== VMC-Chatbot-Pro ===

METRICS DASHBOARD:
- Langfuse: LLM calls, costs, latency
- Custom: Request rate, error rate, p95 latency
- Alerts: Slack/PagerDuty for critical metrics
- Retention: 90 days of metrics data

[Rest same as v49]
```

## Iterations 51-60: Edge Cases

## Iteration 51 (v51) - Added Error Scenarios
**Improvement**: Specified error handling for edge cases
```
=== VMC-Chatbot-Pro ===

ERROR SCENARIOS:
- LLM timeout: Return cached response or fallback message
- Vector store down: Fallback to keyword search
- Database down: Degraded mode (no persistence)
- Rate limit hit: Queue request or return 429
- Invalid input: Return 400 with validation errors

[Rest same as v50]
```

## Iteration 52 (v52) - Added Fallback Mechanisms
**Improvement**: Specified fallback strategies
```
=== VMC-Chatbot-Pro ===

FALLBACKS:
- Primary LLM fails: Switch to LiteLLM failover
- RAG fails: Fallback to direct LLM response
- Cache miss: Proceed without cache
- Observability down: Continue operation (don't block)

[Rest same as v51]
```

## Iteration 53 (v53) - Added Timeout Handling
**Improvement**: Specified timeout strategies
```
=== VMC-Chatbot-Pro ===

TIMEOUTS:
- LLM call: 30s timeout
- Vector search: 5s timeout
- Database query: 10s timeout
- Total request: 60s timeout
- On timeout: Return partial response or error

[Rest same as v52]
```

## Iteration 54 (v54) - Added Retry Logic
**Improvement**: Specified retry strategies
```
=== VMC-Chatbot-Pro ===

RETRIES:
- Transient errors: Retry with exponential backoff (1s, 2s, 4s)
- Max attempts: 3 retries
- Non-retryable: 4xx errors (client errors)
- Retryable: 5xx errors, network timeouts
- Circuit breaker: Stop retrying if failure rate >50%

[Rest same as v53]
```

## Iteration 55 (v55) - Added Input Sanitization
**Improvement**: Specified input cleaning
```
=== VMC-Chatbot-Pro ===

INPUT SANITIZATION:
- Remove control characters
- Trim whitespace
- Validate encoding (UTF-8)
- Max length: 1000 characters
- Escape special characters for SQL/HTML

[Rest same as v54]
```

## Iteration 56 (v56) - Added Output Validation
**Improvement**: Specified output checks
```
=== VMC-Chatbot-Pro ===

OUTPUT VALIDATION:
- Validate LLM response with Zod schema
- Check for PII leakage in output
- Verify response length (max 5000 chars)
- Ensure valid JSON if structured response
- Filter toxic content before sending

[Rest same as v55]
```

## Iteration 57 (v57) - Added Concurrency Control
**Improvement**: Specified concurrency limits
```
=== VMC-Chatbot-Pro ===

CONCURRENCY:
- Max concurrent LLM calls: 10 per instance
- Queue: Use Bull or similar for request queuing
- Priority: Authenticated users > anonymous
- Throttling: Per-user concurrent request limit

[Rest same as v56]
```

## Iteration 58 (v58) - Added Data Privacy
**Improvement**: Specified privacy requirements
```
=== VMC-Chatbot-Pro ===

PRIVACY:
- PII detection: Before processing, mask/remove PII
- Data minimization: Only store necessary data
- Encryption: Encrypt sensitive data at rest
- Access control: Role-based access (RBAC)
- Audit: Log all data access

[Rest same as v57]
```

## Iteration 59 (v59) - Added Internationalization
**Improvement**: Specified i18n support
```
=== VMC-Chatbot-Pro ===

I18N:
- Language detection: Auto-detect user language
- Multi-language: Support ES, EN, PT
- Translations: Store in i18n files
- Locale-aware: Date/time formatting
- RTL support: Right-to-left languages (future)

[Rest same as v58]
```

## Iteration 60 (v60) - Added Analytics
**Improvement**: Specified analytics requirements
```
=== VMC-Chatbot-Pro ===

ANALYTICS:
- User interactions: Track query types, response times
- Success metrics: Task completion rate
- Error tracking: Error types and frequencies
- Usage patterns: Peak hours, popular queries
- Privacy: Anonymize user data

[Rest same as v59]
```

## Iterations 61-70: Advanced Patterns

## Iteration 61 (v61) - Added Plugin Architecture
**Improvement**: Specified plugin system
```
=== VMC-Chatbot-Pro ===

PLUGINS:
- Plugin interface: IPlugin with register() method
- Dynamic loading: Load plugins from packages/plugins/
- Plugin registry: Central registry for all plugins
- Lifecycle: init → execute → cleanup hooks
- Example: Custom tools as plugins

[Rest same as v60]
```

## Iteration 62 (v62) - Added Middleware Pattern
**Improvement**: Specified middleware chain
```
=== VMC-Chatbot-Pro ===

MIDDLEWARE:
- Chain: Request → Auth → RateLimit → Guardrails → Orchestrator → Response
- Order: Execute in defined order
- Early exit: Middleware can short-circuit request
- Context: Pass context object through chain
- Example: Auth middleware validates token before processing

[Rest same as v61]
```

## Iteration 63 (v63) - Added Event System
**Improvement**: Specified event-driven architecture
```
=== VMC-Chatbot-Pro ===

EVENTS:
- Event emitter: Use EventEmitter or similar
- Events: request.received, response.generated, error.occurred
- Listeners: Logging, analytics, notifications
- Async: Events processed asynchronously
- Error handling: Event errors don't block main flow

[Rest same as v62]
```

## Iteration 64 (v64) - Added State Management
**Improvement**: Specified state handling
```
=== VMC-Chatbot-Pro ===

STATE:
- Conversation state: Store in PostgreSQL
- Session state: In-memory with Redis backup
- Cache state: Redis for frequent queries
- State transitions: Documented state machine
- Persistence: Save state on conversation end

[Rest same as v63]
```

## Iteration 65 (v65) - Added Workflow Engine
**Improvement**: Specified workflow patterns
```
=== VMC-Chatbot-Pro ===

WORKFLOWS:
- Workflow definition: YAML or JSON config
- Steps: Sequential or parallel execution
- Conditions: Branch based on conditions
- Retries: Per-step retry configuration
- Example: Multi-step customer support flow

[Rest same as v64]
```

## Iteration 66 (v66) - Added Template System
**Improvement**: Specified template handling
```
=== VMC-Chatbot-Pro ===

TEMPLATES:
- Prompt templates: Store in Langfuse or config files
- Variable substitution: {{variable}} syntax
- Versioning: Track template versions
- A/B testing: Multiple template variants
- Validation: Validate template syntax

[Rest same as v65]
```

## Iteration 67 (v67) - Added Context Management
**Improvement**: Specified context handling
```
=== VMC-Chatbot-Pro ===

CONTEXT:
- Conversation context: Maintain across turns
- User context: Store user preferences, history
- System context: Include system messages
- Context window: Max 4000 tokens
- Context pruning: Remove old messages if limit exceeded

[Rest same as v66]
```

## Iteration 68 (v68) - Added Memory System
**Improvement**: Specified memory architecture
```
=== VMC-Chatbot-Pro ===

MEMORY:
- Short-term: In-memory for active sessions
- Long-term: PostgreSQL for conversation history
- Semantic memory: Vector store for knowledge
- Episodic memory: Store user interactions
- Memory retrieval: RAG for relevant past conversations

[Rest same as v67]
```

## Iteration 69 (v69) - Added Reasoning Chain
**Improvement**: Specified reasoning patterns
```
=== VMC-Chatbot-Pro ===

REASONING:
- Chain-of-thought: Break complex queries into steps
- Self-reflection: LLM reviews its own responses
- Multi-step: Plan → Execute → Verify pattern
- Error correction: Detect and fix errors in reasoning
- Example: "Let me think step by step..."

[Rest same as v68]
```

## Iteration 70 (v70) - Added Tool Calling
**Improvement**: Specified tool integration
```
=== VMC-Chatbot-Pro ===

TOOLS:
- Tool definition: Zod schema + description
- Tool registry: Central registry of available tools
- Tool selection: LLM chooses tools based on query
- Tool execution: Execute with timeout and validation
- Tool results: Format and return to LLM

[Rest same as v69]
```

## Iterations 71-80: Production Hardening

## Iteration 71 (v71) - Added Health Checks
**Improvement**: Specified health check details
```
=== VMC-Chatbot-Pro ===

HEALTH CHECKS:
- Liveness: /health/live (is process running?)
- Readiness: /health/ready (can accept requests?)
- Checks: Database, Redis, LLM API connectivity
- Response: { status: "ok" | "degraded" | "down", checks: {...} }
- Frequency: Kubernetes/load balancer checks every 30s

[Rest same as v70]
```

## Iteration 72 (v72) - Added Graceful Shutdown
**Improvement**: Specified shutdown handling
```
=== VMC-Chatbot-Pro ===

SHUTDOWN:
- Signal handling: SIGTERM, SIGINT
- Grace period: 30s to finish in-flight requests
- Cleanup: Close DB connections, flush logs
- Drain: Stop accepting new requests
- Exit: Process.exit(0) after cleanup

[Rest same as v71]
```

## Iteration 73 (v73) - Added Circuit Breaker
**Improvement**: Specified circuit breaker pattern
```
=== VMC-Chatbot-Pro ===

CIRCUIT BREAKER:
- Threshold: Open circuit if failure rate >50% in 1min
- States: Closed → Open → Half-Open
- Recovery: Try again after 60s (half-open)
- Fallback: Return cached response or error message
- Monitoring: Track circuit state changes

[Rest same as v72]
```

## Iteration 74 (v74) - Added Bulkhead Pattern
**Improvement**: Specified resource isolation
```
=== VMC-Chatbot-Pro ===

BULKHEAD:
- Isolation: Separate thread pools for different operations
- Limits: Max concurrent LLM calls, DB queries, file I/O
- Failure isolation: One failure doesn't affect others
- Resource limits: CPU, memory per operation type
- Monitoring: Track resource usage per bulkhead

[Rest same as v73]
```

## Iteration 75 (v75) - Added Chaos Engineering
**Improvement**: Specified chaos testing
```
=== VMC-Chatbot-Pro ===

CHAOS:
- Tool: Chaos Monkey or similar
- Scenarios: Kill random pods, inject latency, fail DB
- Frequency: Weekly chaos experiments
- Recovery: Verify system recovers automatically
- Documentation: Document chaos test results

[Rest same as v74]
```

## Iteration 76 (v76) - Added Blue-Green Deployment
**Improvement**: Specified deployment strategy
```
=== VMC-Chatbot-Pro ===

DEPLOYMENT:
- Strategy: Blue-green deployment
- Process: Deploy to green, test, switch traffic
- Rollback: Instant switch back to blue
- Testing: Smoke tests on green before switch
- Monitoring: Watch metrics during switch

[Rest same as v75]
```

## Iteration 77 (v77) - Added Canary Releases
**Improvement**: Specified canary deployment
```
=== VMC-Chatbot-Pro ===

CANARY:
- Percentage: Start with 5% traffic to new version
- Monitoring: Watch error rate, latency for 10min
- Gradual: Increase to 25%, 50%, 100% if metrics good
- Rollback: Revert if metrics degrade
- A/B: Compare canary vs baseline metrics

[Rest same as v76]
```

## Iteration 78 (v78) - Added Feature Flags
**Improvement**: Specified feature flag system
```
=== VMC-Chatbot-Pro ===

FEATURE FLAGS:
- Provider: LaunchDarkly, Unleash, or custom
- Flags: Enable/disable features without deploy
- Targeting: Per-user, percentage, custom rules
- Rollout: Gradual rollout (10% → 50% → 100%)
- Monitoring: Track flag usage and impact

[Rest same as v77]
```

## Iteration 79 (v79) - Added Incident Response
**Improvement**: Specified incident procedures
```
=== VMC-Chatbot-Pro ===

INCIDENTS:
- Runbook: Document common incidents and fixes
- Escalation: P1 (critical) → on-call, P2 → next business day
- Communication: Status page for users
- Post-mortem: Document root cause and action items
- Prevention: Update runbook based on incidents

[Rest same as v78]
```

## Iteration 80 (v80) - Added Capacity Planning
**Improvement**: Specified capacity management
```
=== VMC-Chatbot-Pro ===

CAPACITY:
- Monitoring: Track CPU, memory, request rate
- Scaling: Auto-scale based on metrics (CPU >70%)
- Limits: Max instances, max requests per instance
- Forecasting: Predict capacity needs based on trends
- Alerts: Alert when approaching capacity limits

[Rest same as v79]
```

## Iterations 81-90: Advanced Features

## Iteration 81 (v81) - Added Multi-Tenancy
**Improvement**: Specified multi-tenant support
```
=== VMC-Chatbot-Pro ===

MULTI-TENANCY:
- Tenant isolation: Separate data per tenant
- Tenant ID: Include in all requests
- Quotas: Per-tenant rate limits, usage limits
- Billing: Track usage per tenant
- Configuration: Tenant-specific configs

[Rest same as v80]
```

## Iteration 82 (v82) - Added Webhooks
**Improvement**: Specified webhook support
```
=== VMC-Chatbot-Pro ===

WEBHOOKS:
- Events: conversation.started, message.received, error.occurred
- Delivery: Retry with exponential backoff
- Security: HMAC signature verification
- Idempotency: Handle duplicate deliveries
- Logging: Log all webhook deliveries

[Rest same as v81]
```

## Iteration 83 (v83) - Added API Versioning
**Improvement**: Specified versioning strategy
```
=== VMC-Chatbot-Pro ===

VERSIONING:
- URL: /api/v1/chat, /api/v2/chat
- Header: Accept: application/vnd.vmc.v1+json
- Backward compatibility: Support v1 for 6 months
- Deprecation: Announce 3 months before removal
- Migration: Provide migration guide

[Rest same as v82]
```

## Iteration 84 (v84) - Added GraphQL Support
**Improvement**: Specified GraphQL option
```
=== VMC-Chatbot-Pro ===

GRAPHQL:
- Endpoint: /graphql (optional, REST primary)
- Schema: Define Chatbot type, Query, Mutation
- Resolvers: Implement for chat, health queries
- Tools: GraphQL Code Generator for type safety
- Documentation: Auto-generated GraphQL docs

[Rest same as v83]
```

## Iteration 85 (v85) - Added WebSocket Support
**Improvement**: Specified real-time communication
```
=== VMC-Chatbot-Pro ===

WEBSOCKET:
- Endpoint: ws://api/chat (for real-time)
- Protocol: JSON messages
- Events: message, typing, error
- Reconnection: Auto-reconnect with exponential backoff
- Fallback: SSE if WebSocket unavailable

[Rest same as v84]
```

## Iteration 86 (v86) - Added Batch Processing
**Improvement**: Specified batch operations
```
=== VMC-Chatbot-Pro ===

BATCH:
- Endpoint: POST /api/chat/batch
- Input: Array of queries
- Processing: Process in parallel (max 10 concurrent)
- Response: Array of responses with same order
- Rate limit: Higher limit for batch (1000/hour)

[Rest same as v85]
```

## Iteration 87 (v87) - Added Export/Import
**Improvement**: Specified data export
```
=== VMC-Chatbot-Pro ===

EXPORT/IMPORT:
- Export: JSON format with conversations, messages
- Import: Validate schema before import
- Use case: Migration, backup, analytics
- Privacy: User consent required for export
- Format: Standardized JSON schema

[Rest same as v86]
```

## Iteration 88 (v88) - Added Search Functionality
**Improvement**: Specified search features
```
=== VMC-Chatbot-Pro ===

SEARCH:
- Endpoint: GET /api/search?q=query
- Types: Semantic search (vector), keyword search
- Filters: By date, user, conversation
- Pagination: Cursor-based pagination
- Ranking: Relevance score in results

[Rest same as v87]
```

## Iteration 89 (v89) - Added Admin Dashboard
**Improvement**: Specified admin interface
```
=== VMC-Chatbot-Pro ===

ADMIN:
- Dashboard: Metrics, logs, user management
- Authentication: Admin-only access (RBAC)
- Features: View conversations, manage users, configure system
- Audit: Log all admin actions
- UI: Next.js admin panel (separate route)

[Rest same as v88]
```

## Iteration 90 (v90) - Added Custom Models
**Improvement**: Specified model customization
```
=== VMC-Chatbot-Pro ===

MODELS:
- Support: OpenAI, Anthropic, LiteLLM (multi-provider)
- Fine-tuning: Support custom fine-tuned models
- Model selection: Per-request or per-tenant
- Fallback: Switch to backup model if primary fails
- Cost optimization: Use cheaper models for simple queries

[Rest same as v89]
```

## Iterations 91-100: Final Optimizations

## Iteration 91 (v91) - Added Prompt Versioning
**Improvement**: Specified prompt management
```
=== VMC-Chatbot-Pro ===

PROMPTS:
- Storage: Langfuse for prompt versioning
- Versioning: Semantic versioning (v1.0.0)
- A/B testing: Compare prompt versions
- Rollback: Revert to previous prompt version
- Analytics: Track performance per prompt version

[Rest same as v90]
```

## Iteration 92 (v92) - Added Evaluation Framework
**Improvement**: Specified eval system
```
=== VMC-Chatbot-Pro ===

EVALUATION:
- Framework: Promptfoo for automated evals
- Metrics: Accuracy, latency, cost, toxicity
- Test suite: Comprehensive test cases
- CI integration: Run evals on every PR
- Reporting: Generate eval reports in CI

[Rest same as v91]
```

## Iteration 93 (v93) - Added Continuous Learning
**Improvement**: Specified learning loop
```
=== VMC-Chatbot-Pro ===

LEARNING:
- Feedback: Collect user feedback (thumbs up/down)
- Analysis: Analyze feedback patterns
- Improvement: Update prompts based on feedback
- Testing: Test improvements before deployment
- Monitoring: Track improvement metrics

[Rest same as v92]
```

## Iteration 94 (v94) - Added Synthetic Data
**Improvement**: Specified synthetic data generation
```
=== VMC-Chatbot-Pro ===

SYNTHETIC DATA:
- Generation: Use LLM to generate test conversations
- Use case: Testing, evaluation, training
- Quality: Validate synthetic data quality
- Diversity: Ensure diverse test cases
- Storage: Store in test dataset

[Rest same as v93]
```

## Iteration 95 (v95) - Added Human-in-the-Loop
**Improvement**: Specified HITL support
```
=== VMC-Chatbot-Pro ===

HITL:
- Escalation: Escalate complex queries to humans
- Interface: Admin interface for human review
- Approval: Human approves/rejects responses
- Learning: Use human feedback to improve
- Queue: Manage human review queue

[Rest same as v94]
```

## Iteration 96 (v96) - Added Explainability
**Improvement**: Specified explainability features
```
=== VMC-Chatbot-Pro ===

EXPLAINABILITY:
- Reasoning: Show LLM reasoning chain
- Sources: Cite sources for RAG responses
- Confidence: Show confidence scores
- Transparency: Explain why specific response was chosen
- Debug mode: Detailed logs for debugging

[Rest same as v95]
```

## Iteration 97 (v97) - Added Customization
**Improvement**: Specified customization options
```
=== VMC-Chatbot-Pro ===

CUSTOMIZATION:
- Branding: Custom logo, colors, name
- Personality: Configurable chatbot personality
- Responses: Custom response templates
- Tools: Add custom tools per tenant
- Workflows: Custom conversation flows

[Rest same as v96]
```

## Iteration 98 (v98) - Added Integration Hub
**Improvement**: Specified integration system
```
=== VMC-Chatbot-Pro ===

INTEGRATIONS:
- CRM: Salesforce, HubSpot integration
- Support: Zendesk, Intercom integration
- Analytics: Mixpanel, Amplitude integration
- Storage: S3, Google Cloud Storage
- APIs: REST API for custom integrations

[Rest same as v97]
```

## Iteration 99 (v99) - Added Marketplace
**Improvement**: Specified marketplace concept
```
=== VMC-Chatbot-Pro ===

MARKETPLACE:
- Plugins: Community-contributed plugins
- Templates: Pre-built conversation templates
- Tools: Reusable tool library
- Sharing: Share custom configurations
- Rating: Rate and review plugins/templates

[Rest same as v98]
```

## Iteration 100 (v100) - FINAL OPTIMIZED PROMPT
**Improvement**: Ultimate consolidated version with all best practices
```
=== VMC-Chatbot-Pro: Production Chatbot Monorepo ===

CONTEXT:
Integrate matiasportugau-ui repos (ChatBOT, background-agents, Dashboard-bmc) into unified production chatbot following Rasa/Botpress/LangChain/Haystack/LlamaIndex patterns. Target: ≥90% eval pass, p95 latency ≤2.5s, RAG hallucination ≤5%.

PRIORITY STRUCTURE:
1. MVP: packages/core/orchestrator.ts, packages/rag/graph.ts, .github/workflows/ci.yml, promptfoo.yaml
2. Production: packages/guardrails/, packages/observability/, packages/monitoring/
3. Scale: packages/channels/, packages/db/, docker-compose.yml

FILE STRUCTURE:
packages/core/orchestrator.ts  // Intent router: Router(intent) → RAG | Tool | LLM (timeout 5s, retry 3x)
packages/tools/index.ts  // Tool registry with Zod schemas
packages/rag/graph.ts  // RAGGraph: embed → retrieve → generate (provenance validation)
packages/guardrails/  // PII detection, toxicity filter, injection detection
packages/observability/  // Langfuse (cost tracking) + OpenTelemetry (tracing)
packages/channels/  // Web (Next.js 15 + React 19), Mobile (REST API)
packages/monitoring/  // Health (/health), metrics (Prometheus), alerts
packages/db/  // Drizzle schema (conversations, messages, user_sessions) + migrations
docs/  // research_v1.md, matriz_repos.csv, security_report.md, checklists
.github/workflows/ci.yml  // Lint → Type check → Test (≥80%) → Eval (≥90%) → Build → Security → Deploy
docker-compose.yml  // Services: app, postgres:15, redis:7-alpine
vercel.json  // Edge deployment with env vars
promptfoo.yaml  // Eval config (≥90% target)
.env.example  // Template (DATABASE_URL, REDIS_URL, OPENAI_API_KEY, LANGFUSE_SECRET_KEY, NODE_ENV)

CODE EXAMPLE (orchestrator.ts):
```typescript
import { z } from 'zod';
import { RAGGraph } from '../rag/graph';
import { ToolRegistry } from '../tools';
import { Langfuse } from '../observability/langfuse';

const InputSchema = z.object({ query: z.string().min(1).max(1000) });

export class Orchestrator {
  constructor(
    private ragGraph: RAGGraph,
    private tools: ToolRegistry,
    private llm: LLM
  ) {}

  async handleRequest(input: string): Promise<string> {
    const trace = Langfuse.trace({ input });
    try {
      const validated = InputSchema.parse({ query: input });
      const intent = await this.detectIntent(validated.query);
      let result: string;
      if (intent === 'rag') {
        result = await Promise.race([
          this.ragGraph.retrieveAndGenerate(validated.query),
          this.timeout(5000)
        ]);
      } else if (intent === 'tool') {
        result = await this.tools.execute(validated.query);
      } else {
        result = await this.llm.generate(validated.query);
      }
      trace.end({ output: result, latency: Date.now() - startTime });
      return result;
    } catch (error) {
      trace.end({ error: error.message });
      this.logger.error('Request failed', { input, error });
      throw new UserFacingError('Sorry, something went wrong');
    }
  }
}
```

TECH STACK:
Node.js 20.x | TypeScript 5.x (strict mode) | Next.js 15.0.0 | React 19.0.0 | Drizzle ORM 0.29.0 | PostgreSQL 15 | Redis 7

DEPENDENCIES:
npm install --save-dev typescript@5.3.3 ts-node@10.9.2 @types/node@20.10.0 promptfoo@latest jest@29.7.0 vitest@1.0.0 eslint@latest prettier@latest
npm install --save drizzle-orm@0.29.0 @vercel/ai-sdk@2.4.0 next@15.0.0 react@19.0.0 react-dom@19.0.0 zod@3.22.4 langfuse@latest @opentelemetry/api@latest dotenv@16.3.1 @neondatabase/serverless@latest

QUALITY REQUIREMENTS:
✅ TypeScript strict mode, ESLint zero errors, Prettier formatting
✅ Test coverage ≥80% (Jest/Vitest), Promptfoo evals ≥90% pass rate
✅ All async operations: 5s timeout, max 3 retries with exponential backoff
✅ All inputs: Zod schema validation, max 1000 chars, sanitized
✅ All errors: try/catch with structured logging (no stack traces to users)
✅ All exports: Named exports for classes, default exports for utilities
✅ All functions: JSDoc comments for public APIs
✅ All secrets: Environment variables only (never hardcoded)

PERFORMANCE:
- Latency: p95 ≤2.5s (first token), ≤6s (complete response)
- Caching: Redis for frequent queries (TTL: 5min)
- Streaming: SSE for real-time responses (@vercel/ai-sdk)
- Bundle: <500KB gzipped, code splitting, lazy loading
- Connection pooling: PostgreSQL max 20 connections

SECURITY:
- Input sanitization, PII detection, toxicity filtering
- Rate limiting: 100 req/min per IP, 1000 req/hour per user
- CORS: Specific origins only
- Secrets: .env (gitignored), Vercel secrets for production
- Dependency audit: npm audit (zero high/critical vulnerabilities)
- Secret scanning: GitHub Dependabot enabled

OBSERVABILITY:
- Langfuse: All LLM calls logged with cost tracking
- OpenTelemetry: Distributed tracing for all async operations
- Health checks: GET /health (liveness + readiness)
- Metrics: Prometheus format, p50/p95/p99 latency
- Alerts: Slack/PagerDuty for critical errors

DEPLOYMENT:
- Vercel Edge: Primary deployment (vercel.json)
- Docker Compose: Full stack for local/dev (postgres + redis)
- CI/CD: GitHub Actions (lint → test → eval → build → deploy)
- Rollback: Automatic if KPIs fail (p95 >6s OR error rate >5% OR evals <90%)
- Blue-green: Zero-downtime deployments

MULTI-CHANNEL:
- Web: Next.js 15 + React 19 with SSE streaming
- Mobile: REST API compatible
- Future: Slack, WhatsApp, Telegram adapters

This prompt incorporates 100 iterations of refinement following prompt engineering best practices: clarity, specificity, examples, delimiters, context, format specifications, error handling, and comprehensive requirements.
```
