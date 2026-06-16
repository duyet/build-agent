# build-agent

You are helping build an AI-agent application. Follow the canonical skill at
`skills/build-agent/SKILL.md` in this repository.

Procedure:
1. **Entry mode** — if the repo is empty or the user says "from scratch",
   interview them deeply using `skills/build-agent/workflows/from-scratch.md`.
   If a project already exists, detect the techstack first
   (`skills/build-agent/workflows/from-existing.md`) and confirm before adding.
2. **Interview** (scratch mode) — gather purpose/use case, language, framework,
   architecture, model+provider, tools, UI/UX, persistence, observability, and
   deploy target (Docker / VM / k3s / cloud / Cloudflare Workers / Vercel).
   Restate the spec before building.
3. **Choose a framework** with a one-line rationale (LangGraph, DeepAgents,
   Vercel AI SDK, Cloudflare Agents, TanStack AI, Google ADK, Claude Agent SDK).
4. **Verify against live docs** (Context7 / llms.txt / WebFetch / installed
   package) before writing any framework code — never rely on memory.
5. **Scaffold** the minimum that runs, then layer: agent core → tools → model
   access (gateway?) → API → UI → persistence → observability → deploy. Verify
   each layer runs before moving on.

Reference material: `skills/build-agent/references/` (frameworks, concepts:
tool-calling / tracking / ai-gateways / skills, and model engineering).

$ARGUMENTS
