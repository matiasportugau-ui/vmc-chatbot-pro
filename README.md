# README – Integrador VMC Chatbot Pro

## Objetivo general  

Construir el chatbot “VM C-Chatbot-Pro” integrando todos los repos de la organización `matiasportugau-ui`, así como las mejores prácticas de la comunidad open-source, con una arquitectura de producción robusta (observabilidad, guardrails, RAG, CI/CD, multi-canal) y desplegarlo completamente.

## Roles &amp; responsabilidades  

| Rol                  | Responsabilidades clave |

|-----------------------|-------------------------|

| **Researcher**        | Estudiar repos de referencia open-source de chatbots (ej. Rasa, Botpress, LangChain) para extraer patrones de arquitectura, modularidad, productividad. |

| **Auditor-Repos**     | Listar todos los repos de la organización `matiasportugau-ui` vía API GitHub, analizar lenguaje, tests, modularidad, última actividad, licencias y generar matriz de candidatos. |

| **Architect**         | A partir de los hallazgos anteriores, diseñar la arquitectura del nuevo monorepo o rama, definir estructura de carpetas, capas, contratos y stack tecnológico. |

| **Integrator**        | Crear el repo o rama `vmc-chatbot-pro` o `integracion-vmc`, construir estructura inicial, importar módulos seleccionados, instalar dependencias clave, implementar orquestador/flujo. |

| **Quality-Gate**      | Configurar suite de evaluación automática (con Promptfoo), definir KPIs/SLOs, montar pipeline de CI/CD con gates de calidad. |

| **DevOps-Deployer**   | Configurar despliegue (Vercel Edge / Docker Compose), observabilidad con Langfuse + OpenTelemetry, alertas, runbook, rollback y gobernanza de prompts. |

## Objetivos específicos  

- Investigar al menos **5 proyectos open-source** de chatbots de calidad para documentar buenas prácticas.  

- Auditar todos los repos de `matiasportugau-ui`, seleccionar al menos 3 módulos reutilizables.  

- Construir un MVP funcional dentro de `vmc-chatbot-pro` con arquitectura definida.  

- Configurar guardrails, observabilidad, CI/CD, deploy al menos a entorno de staging.  

- Ejecutar **5 iteraciones** de mejora continua hasta alcanzar readiness para producción.

## Bucle de iteraciones  

| Iteración | Enfoque                          | Salidas esperadas |

|-----------|----------------------------------|-------------------|

| 1         | Investigación comunitaria + mapeo interno | `docs/research_v1.md`, `docs/matriz_repos.csv`, `docs/arquitectura_v1.png` |

| 2         | Integración MVP (importación de módulos)  | Monorepo + estructura inicial, `packages/core/orchestrator.ts`, `packages/tools/...` |

| 3         | Calidad + Evaluaciones CI/CD             | `promptfoo.yaml`, `.github/workflows/ci.yml`, primer reporte de evals |

| 4         | Hardening, rendimiento y escalabilidad   | `packages/rag/graph.ts`, reports de seguridad, docs de UX |

| 5         | Producción + Operación                   | `vercel.json`/`docker-compose.yml`, `docs/post_deploy_checklist.md`, informe final de readiness |

## Arquitectura objetivo  

- **Frontend**: Next.js 15 + React 19 + Vercel AI SDK (SSE streaming)  

- **Backend**: Node 20 + TypeScript + Drizzle ORM + PostgreSQL (Neon) + Redis opcional  

- **AI Gateway**: OpenAI / LiteLLM (failover) con trazabilidad Langfuse  

- **RAG**: Embeddings + vector store + retrieving graph + validador de provenance  

- **Orquestador**: Router de intención → (RAG | Tool | LLM) con contratos Zod, timeouts y retries  

- **Guardrails**: hai-guardrails / Guardrails AI (PII, inyección, toxicity)  

- **Observabilidad**: OpenTelemetry + Langfuse dashboards &amp; coste por llamada  

- **CI/CD**: GitHub Actions (lint, test, evals, build, deploy)  

- **Deployment**: Vercel Edge y/o Docker Compose para stack completo

## KPIs / SLOs  

- Tasa de aprobación funcional (Promptfoo): ≥ 90%  

- Latencia p95: ≤ 2.5 s (respuesta inicial SSE) / ≤ 6 s (respuesta completa)  

- Tasa de alucinaciones RAG: ≤ 5%  

- Coste por turno: dentro del presupuesto definido  

- Error en pipeline CI: &lt; 5%  

- Módulos integrados: ≥ 3  

- Soporte multi-canal habilitado: ✔

## Pasos de ejecución inmediata  

1. Crear repo (o rama) `vmc-chatbot-pro` o `integracion-vmc`.  

2. Pegar este README como punto de partida.  

3. Iniciar la **iteración 1** usando los roles Researcher + Auditor-Repos.  

   - Generar `docs/research_v1.md` con al menos 5 proyectos comunitarios.  

   - Generar `docs/matriz_repos.csv` con el análisis de tus repos.  

4. Revisar salidas, decidir módulos reutilizables, votar por integración.  

5. Avanzar a **iteración 2**, y así sucesivamente.

## Gobernanza y seguridad  

- Control de dependencias: auditarlas automáticamente.  

- Escaneo de secretos y riesgos de seguridad: habilitar secret scan.  

- Versionado de prompts: utilizar Langfuse MCP para prompts en producción.  

- Aprobaciones de merges: mínimo 2 aprobadores para main / production.  

- Pipeline de rollback automático si KPIs no se cumplen post-deploy.

---

&gt; **Nota:** Los agentes en Cursor pueden ser configurados para esta tarea. Asegúrate de tener acceso a la organización GitHub, conectar Langfuse/Promptfoo, y reservar recursos para CI/CD y despliegue. Consulta la documentación de Cursor para referencia de modos/agent tools.  [oai_citation:0‡docs.cursor.com](https://docs.cursor.com/agent/overview?utm_source=chatgpt.com)
