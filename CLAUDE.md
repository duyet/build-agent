# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

This repo is **content, not an app** — no build/test/lint. It packages one Agent
Skill (`skills/build-agent/`) distributed as a Claude plugin
(`.claude-plugin/plugin.json`) and a Codex plugin (`codex/`).

## Single source of truth
`skills/build-agent/SKILL.md` is canonical. The Codex adapter (`codex/AGENTS.md`,
`codex/prompts/build-agent.md`) only **points** at it — never duplicate skill
logic there. Change behavior in `SKILL.md` and the workflows/references, not in
the adapters.

## Editing the references
`skills/build-agent/references/**` is deliberately **thin: glossary + live-doc
links**, to avoid going stale. When editing:
- Keep framework files to concepts + canonical URLs; don't paste full API docs.
- If a section starts mirroring real API docs, trim it and link out instead.
- Treat any code snippet as illustrative; the skill must verify against live
  docs (Context7 / `llms.txt` / WebFetch) before generating code.

## Validating the skill
Use the `skill-creator` skill/plugin to lint frontmatter and test triggering:
`/skill-creator build-agent`. The `description` in `SKILL.md` is the trigger
router — keep it dense with real user phrasings.
