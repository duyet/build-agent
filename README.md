# build-agent

A single **Agent Skill** that knows how to build AI-agent applications
end-to-end — from an empty repo or an existing codebase. It interviews you when
requirements are unclear, detects your stack when a project already exists, then
scaffolds the agent loop, tools, API, UI/UX, observability, and deployment.

It knows **LangGraph, DeepAgents, Vercel AI SDK, Cloudflare Agents SDK, TanStack
AI, Google ADK, and the Claude Agent SDK** — and the cross-cutting concepts:
building skills, tool calling, tracking/observability, and AI gateways
(OpenRouter, AnyRouter, Cloudflare AI Gateway).

The idea: **don't hardcode framework APIs that go stale.** The skill keeps a thin
glossary + a live-doc index and always verifies against official sources
(Context7 / `llms.txt` / WebFetch / the installed package) before writing code.
Ships as both a **Claude plugin** and a **Codex plugin** over one shared skill.

# Install

```
npx skills add duyet/build-agent
```

Works in any agent that supports the Agent Skills format. The plans it writes are
plain markdown, so any agent (or human) can pick them up.

<details>
<summary>Install in Claude Code (plugin)</summary>

Add this repo as a plugin marketplace, then install the plugin:

```
/plugin marketplace add duyet/build-agent
/plugin install build-agent@build-agent
```

That registers the `.claude-plugin/plugin.json` and exposes the
`skills/build-agent` skill. Then just describe what you want — the skill
triggers on intent (see [Usage](#usage)), or force it with `/build-agent`.
</details>

<details>
<summary>Install in Codex</summary>

Clone the repo, then point Codex at the adapter:

```
git clone https://github.com/duyet/build-agent
```

- Add `build-agent/codex/AGENTS.md` to your project (or merge its pointer into
  your own `AGENTS.md`), **or**
- Load `build-agent/codex/prompts/build-agent.md` as a custom prompt to kick off
  the workflow.

Both reference the same canonical `skills/build-agent/SKILL.md` — no duplicated
logic.
</details>

# Usage

Just describe what you want — the skill triggers on intent:

```
build me an agent
scaffold an AI agent app from scratch
add an agent API to this Next.js app
build a streaming chat UI for my agent
which agent framework should I use?
set up tool calling / tracing / an AI gateway for my agent
```

**From scratch** → it interviews you (purpose, language, framework,
architecture, model/provider, tools, UI, persistence, observability, deploy
target) and then builds.

**From an existing project** → it detects your techstack, confirms it, and adds
agent code that matches your conventions.

# How it works

```
build-agent/
├── .claude-plugin/plugin.json        # Claude plugin manifest
├── codex/                            # Codex adapter (AGENTS.md + prompt)
└── skills/build-agent/
    ├── SKILL.md                      # the canonical skill (shared by both)
    ├── workflows/
    │   ├── from-scratch.md           # deep interview flow
    │   └── from-existing.md          # techstack-detection flow
    └── references/                   # thin glossary + live-doc links
        ├── frameworks/               # langgraph, deepagents, ai-sdk,
        │                             #   cloudflare-agents, tanstack-ai,
        │                             #   google-adk, claude-agent-sdk
        ├── concepts/                 # skills, tool-calling,
        │                             #   tracking-observability, ai-gateways
        └── engineering/              # claude, gemini, gpt prompting
```

1. **Entry mode** — empty repo → interview; existing repo → detect + confirm.
2. **Choose a framework** — recommends one with a one-line rationale; you decide.
3. **Verify before building** — pulls current docs (Context7 / `llms.txt` /
   WebFetch) so it never ships stale API code.
4. **Scaffold in layers** — agent core → tools → model access → API → UI →
   persistence → observability → deploy, verifying each layer runs.

### Example end states it can build
- LangGraph supervisor (Python) with checkpointing, deployed on Docker/k3s.
- Next.js + Vercel AI SDK streaming chat with tool calls and generative UI on
  Vercel.
- Cloudflare Agents SDK durable agent on Workers, state in Durable Objects.
- Claude Agent SDK coding agent with subagents, MCP tools, and hooks.
- Google ADK multi-agent (Gemini) with built-in evals on Cloud Run.
- Any of the above behind an OpenRouter / AnyRouter gateway with tracing + cost
  tracking wired from day one.

# License

MIT © duyet
