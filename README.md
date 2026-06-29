# build-agent

A single **Agent Skill** that knows how to build AI-agent applications
end-to-end — from an empty repo or an existing codebase. It interviews you when
requirements are unclear, detects your stack when a project already exists, then
scaffolds the agent loop, tools, API, UI/UX, observability, and deployment.

It knows **[LangGraph](https://langchain-ai.github.io/langgraph/),
[DeepAgents](https://github.com/langchain-ai/deepagents),
[Vercel AI SDK](https://ai-sdk.dev/docs),
[Cloudflare Agents SDK](https://developers.cloudflare.com/agents/),
[TanStack AI](https://tanstack.com/ai),
[Google ADK](https://google.github.io/adk-docs/), the
[Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk/overview),
[Eve](https://github.com/vercel/eve),
[Flue](https://flueframework.com/), and
[Pi](https://pi.dev/)** — and the
cross-cutting concepts: building skills, tool calling, tracking/observability,
and AI gateways ([OpenRouter](https://openrouter.ai/),
[AnyRouter](https://anyrouter.dev/docs.md),
[Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/)).

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
<summary>Install in Codex (plugin)</summary>

**Codex CLI** — add this repo as a marketplace and install the plugin:

```
/plugin marketplace add duyet/build-agent
/plugin install build-agent@build-agent
/reload-plugins
```

`/plugins` opens the browser to search/install interactively, and
`@branch` / `#tag` pin a version. The plugin is defined by
`.codex-plugin/plugin.json` and exposes the shared `skills/build-agent` skill.

**Codex App** — search/browse for **build-agent**, open its details, and click
**Install** → **Add to Codex**.

**Manual / headless** — clone the repo and either add `codex/AGENTS.md` to your
project (or merge its pointer into your own `AGENTS.md`), or load
`codex/prompts/build-agent.md` as a custom prompt. All paths reference the same
canonical `skills/build-agent/SKILL.md` — no duplicated logic.
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
        │                             #   google-adk, claude-agent-sdk,
        │                             #   eve, flue, pi
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

# Frameworks & references

The skill keeps a thin glossary per framework that **links out to the official,
up-to-date docs** (and verifies against them before writing code). Official docs
on the left, the in-repo reference on the right:

| Framework | Official docs | In-repo glossary |
|-----------|---------------|------------------|
| [LangGraph](https://langchain-ai.github.io/langgraph/) | [langchain-ai.github.io/langgraph](https://langchain-ai.github.io/langgraph/) · [llms.txt](https://langchain-ai.github.io/langgraph/llms.txt) | [langgraph.md](skills/build-agent/references/frameworks/langgraph.md) |
| [DeepAgents](https://github.com/langchain-ai/deepagents) | [github.com/langchain-ai/deepagents](https://github.com/langchain-ai/deepagents) · [js](https://github.com/langchain-ai/deepagentsjs) | [deepagents.md](skills/build-agent/references/frameworks/deepagents.md) |
| [Vercel AI SDK](https://ai-sdk.dev/docs) | [ai-sdk.dev/docs](https://ai-sdk.dev/docs) · [llms.txt](https://ai-sdk.dev/llms.txt) | [ai-sdk.md](skills/build-agent/references/frameworks/ai-sdk.md) |
| [Cloudflare Agents SDK](https://developers.cloudflare.com/agents/) | [developers.cloudflare.com/agents](https://developers.cloudflare.com/agents/) · [llms](https://developers.cloudflare.com/agents/llms-full.txt) | [cloudflare-agents.md](skills/build-agent/references/frameworks/cloudflare-agents.md) |
| [TanStack AI](https://tanstack.com/ai) | [tanstack.com/ai](https://tanstack.com/ai) | [tanstack-ai.md](skills/build-agent/references/frameworks/tanstack-ai.md) |
| [Google ADK](https://google.github.io/adk-docs/) | [google.github.io/adk-docs](https://google.github.io/adk-docs/) · [llms.txt](https://google.github.io/adk-docs/llms.txt) | [google-adk.md](skills/build-agent/references/frameworks/google-adk.md) |
| [Claude Agent SDK](https://docs.claude.com/en/api/agent-sdk/overview) | [docs.claude.com/…/agent-sdk](https://docs.claude.com/en/api/agent-sdk/overview) | [claude-agent-sdk.md](skills/build-agent/references/frameworks/claude-agent-sdk.md) |
| [Eve](https://github.com/vercel/eve) | [eve.dev/docs](https://eve.dev/docs) · [repo](https://github.com/vercel/eve) | [eve.md](skills/build-agent/references/frameworks/eve.md) |
| [Flue](https://flueframework.com/) | [flueframework.com/docs](https://flueframework.com/docs/) · [intro](https://blog.cloudflare.com/agents-platform-flue-sdk/) | [flue.md](skills/build-agent/references/frameworks/flue.md) |
| [Pi](https://pi.dev/) | [pi.dev/docs/latest](https://pi.dev/docs/latest) · [repo](https://github.com/earendil-works/pi) | [pi.md](skills/build-agent/references/frameworks/pi.md) |

**Gateways:** [OpenRouter](https://openrouter.ai/) · [AnyRouter](https://anyrouter.dev/docs.md) · [Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/) — see [ai-gateways.md](skills/build-agent/references/concepts/ai-gateways.md).
**Concepts:** [building skills](skills/build-agent/references/concepts/skills.md) · [tool calling](skills/build-agent/references/concepts/tool-calling.md) · [tracking & observability](skills/build-agent/references/concepts/tracking-observability.md).

# License

MIT © duyet
