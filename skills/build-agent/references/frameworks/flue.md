# Flue

TypeScript framework for **headless, autonomous agents** built on a
**harness-driven** architecture — the same harness pattern Claude Code and other
coding agents use. From the Astro team, originally to automate work inside their
own repos. Good for agents that run without a human present: triggered by API
calls, webhooks, or cron, and deployable to Node.js or Cloudflare Workers.

**Live docs:** https://flueframework.com/ · docs
https://flueframework.com/docs/ · quickstart
https://flueframework.com/docs/getting-started/quickstart/ · Cloudflare intro
https://blog.cloudflare.com/agents-platform-flue-sdk/ · TypeScript (Node
>= 22.19).

## Glossary
- **Harness** — the agent runtime loop Flue wraps with structure + conventions.
- **Agents** — the unit you author and run.
- **Workflows** — orchestration of agent steps.
- **Sandboxes** — isolated execution environments for agent actions.
- **Sessions / tools / skills** — session state, callable tools, on-demand skills.
- **Targets** — deploy configuration (local CI, Node.js, Cloudflare Workers).
- **Provider access** — LLMs via the Pi SDK (e.g. Claude, Cloudflare models).

## When to choose
You want programmable, headless agents (no chat UI assumed) with a coding-agent
harness, run from CI/webhooks/cron and shipped to Node or Cloudflare. If you want
a filesystem-first convention layout, see Eve; for stateful graphs, LangGraph;
for edge-durable stateful objects, Cloudflare Agents SDK.

## Before coding
Flue is young and moving — confirm the current agent/workflow/sandbox config and
the Pi SDK provider wiring from `flueframework.com/docs` before generating code.
