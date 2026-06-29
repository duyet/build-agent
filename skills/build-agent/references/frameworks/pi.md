# Pi (pi.dev)

Minimal, open-source **agent harness** and **unified LLM toolkit** in TypeScript.
Design thesis is radical minimalism: a tiny system prompt and four tools (read,
write, edit, bash), provider-agnostic and bring-your-own-key, with no built-in
sub-agents, plan mode, or MCP — you add those via extensions/skills/packages.
Ships both a unified multi-provider LLM API and an agent runtime you can embed,
plus an interactive coding-agent CLI. Good when you want a small, inspectable
harness you adapt to your workflow — "many agent harnesses, but this one is
yours." (Pi is the SDK that [Flue](flue.md) builds on.)

**Live docs:** https://pi.dev/ · docs https://pi.dev/docs/latest · repo
https://github.com/earendil-works/pi · install `npm i -g --ignore-scripts
@earendil-works/pi-coding-agent` · MIT · TypeScript.

## Glossary
- **pi-ai** (`@earendil-works/pi-ai`) — unified multi-provider LLM API
  (Anthropic, OpenAI, Google, Bedrock, Vertex, Azure, …).
- **pi-agent-core** (`@earendil-works/pi-agent-core`) — agent runtime: tool
  calling + state management; embed as an SDK.
- **pi-coding-agent** (`@earendil-works/pi-coding-agent`) — the interactive
  coding-agent CLI.
- **pi-tui** (`@earendil-works/pi-tui`) — terminal UI library (differential
  rendering); **pi-web-ui** — web UI component library.
- **Tools** — the four built-ins: read, write, edit, bash.
- **Modes** — interactive, print/JSON, RPC, and SDK.
- **Extensions / skills / packages** — how you add capabilities; bundle and
  share as Pi packages via npm or git.

## When to choose
You want a minimal, provider-agnostic harness to embed (`pi-agent-core`) or a
unified LLM API across providers (`pi-ai`), and you prefer composing
capabilities from extensions over a batteries-included framework. If you want a
headless framework already wrapping this harness with workflows/sandboxes/deploy
targets, use [Flue](flue.md); for a filesystem-first convention layout, see
[Eve](eve.md); for stateful graphs, LangGraph.

## Before coding
Pi is young and iterating — confirm the current package names, tool/mode APIs,
and provider wiring from `pi.dev/docs/latest` (or the package READMEs under
`packages/` in the repo) before generating code.
