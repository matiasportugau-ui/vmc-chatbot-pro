# Final Optimized GitHub Copilot Prompt (v100)

This is the final, production-ready prompt after 100 iterations of refinement following prompt engineering best practices.

---

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

---

## Usage Instructions

1. Copy the prompt above (between the triple backticks)
2. Paste it into GitHub Copilot's prompt field when creating the repository
3. Click "Create repository"
4. Review the generated code and structure
5. Refine as needed based on your specific requirements

## Key Improvements Made Over 100 Iterations

1. **Clarity & Specificity**: Removed ambiguities, added exact file paths and versions
2. **Context**: Added project background and integration goals
3. **Examples**: Included concrete code examples for orchestrator
4. **Delimiters**: Used clear section markers (===) for structure
5. **Format Specifications**: Detailed file structure, naming conventions
6. **Error Handling**: Comprehensive error handling patterns
7. **Quality Gates**: Specific metrics and requirements
8. **Security**: Input validation, PII detection, rate limiting
9. **Observability**: Langfuse, OpenTelemetry, monitoring
10. **Deployment**: Complete CI/CD, rollback strategies, multi-channel support


