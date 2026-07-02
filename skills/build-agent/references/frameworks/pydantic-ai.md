# Pydantic AI

Typed, **Python-first** agent framework from the Pydantic team — "FastAPI feel"
for GenAI. Model-agnostic agents with schema-validated structured output,
dependency injection for tools, plus a graph and durable-execution layer for
long-running work. The lightweight, strongly-typed Python option alongside
LangGraph and Google ADK.

**Live docs:** https://pydantic.dev/docs/ai/ · llms.txt
https://pydantic.dev/docs/ai/llms.txt · pip `pydantic-ai` · Python. (Older
`ai.pydantic.dev` links now 301 to `pydantic.dev/docs/ai/` — a live example of
why this skill verifies URLs before use.)

## Glossary
- **Agent** — model + instructions + tools + typed deps + optional output type.
- **Tools** — functions (with a `RunContext`), native provider tools, toolsets.
- **Dependencies** — typed DI passed into tools/prompts (DB handles, config…).
- **Structured output** — results validated against Pydantic models.
- **Durable execution** — resumable runs via Temporal / DBOS / Prefect / Restate
  and others.
- **Pydantic Graph** — typed state-machine graph (steps, decisions, joins,
  parallel) for complex control flow.
- **Instrumentation** — native OpenTelemetry / Pydantic Logfire tracing.

## When to choose
Python teams that want type safety and Pydantic validation end-to-end, clean
dependency injection, and OTel tracing out of the box — without LangGraph's
graph-first model (though Pydantic Graph is there when you need it). For
Google/Gemini + built-in evals prefer [Google ADK](google-adk.md); for
supervisor/multi-agent graphs, LangGraph.

## Before coding
Confirm the current `Agent`/tool/deps APIs, output-type patterns, and durable
backends against `pydantic.dev/docs/ai/` (or Context7 `pydantic-ai`) — and use
the new canonical domain, not the old `ai.pydantic.dev`.
