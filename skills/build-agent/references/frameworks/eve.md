# Eve (Vercel)

Filesystem-first framework for **durable AI agents**. Core agent capabilities
live in conventional file locations — instructions and skills as Markdown, tools
as TypeScript — and the framework compiles the directory into durable workflows
and wires up channels. Good when you want an inspectable, convention-driven agent
with governance/observability/sandboxed compute built in. (Beta.)

**Live docs:** https://eve.dev/docs · tutorial
https://eve.dev/docs/tutorial/first-agent · repo https://github.com/vercel/eve ·
npm `eve` (docs also ship in `node_modules/eve/docs`) · TypeScript.

## Glossary
- **Instructions** — always-on system prompt, authored in Markdown.
- **Skills** — procedures loaded on demand, authored in Markdown.
- **Tools** — typed functions the model can call, authored in TypeScript.
- **Channels** — message entry points (HTTP, Slack, Discord).
- **Schedules** — recurring cron jobs (TypeScript).
- **Agent config** — model + runtime settings (TypeScript).
- **Durable workflows** — the compiled directory runs as resumable workflows.

## When to choose
You want a convention-over-configuration, filesystem-first agent that's easy to
inspect and operate, deployed on Vercel infrastructure, with enterprise
governance and sandboxed compute included. If you need explicit graph control,
prefer LangGraph; if you want the raw coding-agent harness, see the Claude Agent
SDK or Flue.

## Before coding
Eve is beta and iterating — confirm the current directory layout, tool/skill
signatures, and channel/schedule APIs from `eve.dev/docs` or the package docs in
`node_modules/eve/docs` before generating code.
