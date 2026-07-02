# OpenAI Agents SDK

OpenAI's own **lightweight, few-abstractions** agent framework: define agents
with instructions + tools, hand off between them, guard inputs/outputs, and get
built-in sessions and tracing. The provider-native counterpart to the Claude
Agent SDK and Google ADK — reach for it when GPT / the Responses API is the
center of gravity.

**Live docs:** Python https://openai.github.io/openai-agents-python/ ·
TS/JS https://openai.github.io/openai-agents-js/ ·
Python `openai-agents` · npm `@openai/agents` · host skill: none (use Context7
`openai-agents` or the docs sites).

## Glossary
- **Agent** — model + instructions + tools + optional output type.
- **Handoffs** — delegate the conversation to another agent (routing / triage).
- **Tools** — Python/TS functions, plus hosted tools (web search, file search,
  code interpreter, computer use).
- **Guardrails** — validate/scan inputs and outputs; can trip and halt a run.
- **Sessions** — automatic conversation-history management across turns.
- **Tracing** — built-in run tracing (viewable in the OpenAI dashboard) with
  hooks to export to third-party observability.
- **Realtime / Voice agents** — speech-to-speech and voice pipelines
  (WebSocket / WebRTC / SIP transports).

## When to choose
GPT-first apps, teams already on the OpenAI SDK/Responses API, or when you want
a minimal, unopinionated loop with handoffs and guardrails rather than a graph.
Python and TypeScript are first-class. For stateful graphs prefer LangGraph; for
a batteries-included TS app framework, [Mastra](mastra.md); for Claude-centric
harness features, the [Claude Agent SDK](claude-agent-sdk.md).

## Before coding
Confirm current `Agent`/handoff/guardrail APIs and model ids against the docs
site (or Context7 `openai-agents`) — the SDK iterates and the Python and TS
surfaces differ. Verify hosted-tool availability for your account tier.
