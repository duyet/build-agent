# Mastra

Batteries-included **TypeScript** framework for AI apps and agents: agents,
durable workflows, tools/MCP, memory, RAG, evals, and observability behind one
opinionated stack that runs standalone or inside any JS backend. The
full-framework TS option when the Vercel AI SDK feels too low-level and you're
not tied to Next.js.

**Live docs:** https://mastra.ai/docs · llms.txt https://mastra.ai/llms.txt ·
scaffold `npm create mastra@latest` · core `@mastra/core` · TypeScript
(modern Node LTS).

## Glossary
- **Agent** — model + instructions + tools + memory; can call other agents.
- **Workflows** — durable, graph-like step orchestration with branching,
  suspend/resume, and human-in-the-loop.
- **Tools & MCP** — typed tools; first-class Model Context Protocol client/server.
- **Memory** — message history, semantic recall, and working memory.
- **RAG** — chunking, embeddings, vector-store adapters, GraphRAG.
- **Scorers / Evals** — score outputs and trajectories against datasets.
- **Observability** — built-in tracing, metrics, and logging.
- **Deploy** — standalone server or deployer adapters (Vercel, Cloudflare,
  Node).

## When to choose
You want an integrated TS framework (agents + workflows + memory + RAG + evals)
rather than assembling primitives yourself, especially outside Next.js or as a
standalone agent server. If you mainly need streaming chat UI in a React/Next
app, the [Vercel AI SDK](ai-sdk.md) is lighter; for stateful graphs across
Python/TS, LangGraph; for edge-durable objects, the
[Cloudflare Agents SDK](cloudflare-agents.md).

## Before coding
Fast-moving — confirm the current package split (`@mastra/*`), the
`create mastra` scaffold output, and workflow/memory APIs from `mastra.ai/docs`
(or its `llms.txt`) before generating code.
