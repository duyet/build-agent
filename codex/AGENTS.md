# build-agent — Codex adapter

This is the **Codex plugin** for the `build-agent` skill. Codex has no separate
plugin format, so this adapter points Codex at the **single canonical skill**
shared with the Claude plugin. There is no duplicated logic here — the source of
truth is:

    ../skills/build-agent/SKILL.md

## How Codex should use it
When the user asks to **build / scaffold an AI-agent application**, add an agent
API, build an agent chat/UI, choose an agent framework, or set up tool calling,
tracing, or an AI gateway:

1. Read `../skills/build-agent/SKILL.md` and follow it as the procedure.
2. Determine entry mode → `../skills/build-agent/workflows/from-scratch.md`
   (interview) or `../skills/build-agent/workflows/from-existing.md` (detect).
3. Pull the relevant `../skills/build-agent/references/**` file for the chosen
   framework / concept, then **verify against live official docs** before
   writing code (Context7 / `llms.txt` / WebFetch — whatever Codex has).

## Prompt entry point
A ready-to-use prompt lives at `prompts/build-agent.md` — load it as a custom
prompt/command, or paste it to kick off the workflow.

Keep this file thin. If the skill changes, you change `SKILL.md`, not this.
