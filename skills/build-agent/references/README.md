# references — thin glossary + live-doc index

These files are intentionally small. They tell you **what each framework/concept
is and where the authoritative, up-to-date docs live**. Always fetch the live
docs (Context7 / `llms.txt` / WebFetch) before writing framework code — the
snippets here are illustrative and may lag the latest release.

## Frameworks
| Framework | File | Official docs / llms |
|-----------|------|----------------------|
| LangGraph | `frameworks/langgraph.md` | https://docs.langchain.com/oss/python/langgraph/overview · llms.txt: https://docs.langchain.com/llms.txt |
| DeepAgents | `frameworks/deepagents.md` | https://github.com/langchain-ai/deepagents · JS: https://github.com/langchain-ai/deepagentsjs |
| Pydantic AI | `frameworks/pydantic-ai.md` | https://pydantic.dev/docs/ai/ · llms.txt: https://pydantic.dev/docs/ai/llms.txt |
| Vercel AI SDK | `frameworks/ai-sdk.md` | https://ai-sdk.dev/docs · llms: https://ai-sdk.dev/llms.txt |
| Mastra | `frameworks/mastra.md` | https://mastra.ai/docs · llms: https://mastra.ai/llms.txt |
| Cloudflare Agents SDK | `frameworks/cloudflare-agents.md` | https://developers.cloudflare.com/agents/ · llms: https://developers.cloudflare.com/agents/llms-full.txt |
| TanStack AI | `frameworks/tanstack-ai.md` | https://tanstack.com/ai/latest/docs (blocks fetchers → use Context7) |
| Google ADK | `frameworks/google-adk.md` | https://adk.dev/ · llms: https://adk.dev/llms.txt |
| OpenAI Agents SDK | `frameworks/openai-agents.md` | Python: https://openai.github.io/openai-agents-python/ · JS: https://openai.github.io/openai-agents-js/ |
| Claude Agent SDK | `frameworks/claude-agent-sdk.md` | https://code.claude.com/docs/en/agent-sdk/overview · llms.txt: https://code.claude.com/docs/llms.txt |
| Eve (Vercel) | `frameworks/eve.md` | https://eve.dev/docs · repo: https://github.com/vercel/eve |
| Flue | `frameworks/flue.md` | https://flueframework.com/docs/ · intro: https://blog.cloudflare.com/agents-platform-flue-sdk/ |
| Pi (pi.dev) | `frameworks/pi.md` | https://pi.dev/docs/latest · repo: https://github.com/earendil-works/pi |

## Cross-cutting concepts
| Concept | File |
|---------|------|
| Building skills for agents | `concepts/skills.md` |
| Tool calling | `concepts/tool-calling.md` |
| Tracking / observability | `concepts/tracking-observability.md` |
| AI gateways (OpenRouter / AnyRouter / AI gateway) | `concepts/ai-gateways.md` |

## Model engineering / prompting
| Model family | File |
|--------------|------|
| Claude (Anthropic) | `engineering/claude.md` |
| Gemini (Google) | `engineering/gemini.md` |
| GPT (OpenAI) | `engineering/gpt.md` |

> Maintenance note: keep these files to glossary depth. If a section starts to
> mirror full API docs, trim it and link out instead — staleness is the enemy.
