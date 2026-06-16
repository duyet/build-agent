# DeepAgents

Opinionated "deep agent" pattern built **on top of LangGraph**: a planning agent
with a todo/plan tool, a virtual filesystem, and the ability to spawn
**subagents**. Good for research, coding, and long-horizon tasks that need
planning + delegation rather than a single tool loop.

**Live docs:** https://github.com/langchain-ai/deepagents ·
https://docs.langchain.com/labs/deep-agents/overview ·
Python `deepagents` · JS `deepagents`

## Glossary
- **Planning tool** — lets the agent write/track a todo list (steerable plan).
- **Virtual filesystem** — scratch space the agent reads/writes during a task.
- **Subagents** — delegated agents for focused subtasks; keeps context clean.
- **Built on LangGraph** — you get checkpointing, streaming, human-in-loop for free.

## When to choose
You want the "Claude Code / Manus-style" deep planning loop out of the box,
without hand-building the supervisor + scratchpad + subagent machinery. If you
need full custom control, drop to plain LangGraph.

## Before coding
Confirm the current constructor/config API and default tools from the repo
README — this package iterates quickly.
