# AI Applications & Agents — Learning Notes

Structured learning notes on AI applications, LLMs, prompt engineering, agents, RAG, and multi-agent systems. **Bilingual:** main content in **Chinese (简体中文)**; [English overview](docs/en/index.md) in `docs/en/`. On the doc site, use the **中文** / **English** links at the top of the sidebar to switch.

## Learning Path

The material is organized in six parts. Start from the checklist and follow the links into each note.

| Part | Topic | Main note |
|------|--------|-----------|
| 1 | AI application basics (app types, tech stack, when to use tools) | [AI应用概览](docs/AI应用概览.md) |
| 2 | LLM & prompt engineering (capabilities, limits, prompts, context, cost) | [LLM与提示工程](docs/LLM与提示工程.md) |
| 3 | Agent core (ReAct, Plan-and-Execute, tools, Function Calling) | [Agent架构](docs/Agent架构.md), [工具与Function-Calling](docs/工具与Function-Calling.md) |
| 4 | Memory & RAG (short/long-term memory, retrieval, multi-turn) | [记忆与RAG](docs/记忆与RAG.md) |
| 5 | Multi-agent systems (roles, coordination, messaging) | [多Agent系统](docs/多Agent系统.md) |
| 6 | Engineering & production (frameworks, evaluation, security, deployment) | [Agent工程化](docs/Agent工程化.md) |

**Checklist (syllabus):** [学习清单-AI应用与Agent](docs/学习清单-AI应用与Agent.md)

## How to Use

- **Read only:** Open any `.md` file in a Markdown viewer or on GitHub.
- **With links:** Open this folder as a vault in [Obsidian](https://obsidian.md); `[[note name]]` wikilinks will resolve between notes.

## File Overview

- **Repo root:** `README.md`, `mkdocs.yml`, and this overview.
- **Documentation (and doc site source):** All learning notes live in the [`docs/`](docs/) folder. The GitHub Pages site is built from `docs/` via MkDocs.

```
docs/
  index.md          ← Site home (中文)
  学习清单-AI应用与Agent.md   ← Start here (checklist + links)
  AI应用概览.md
  LLM与提示工程.md
  ... (Part 1–6 notes)
  发布文档指南.md
  en/               ← English
    index.md        ← English home
    learning-checklist.md
    part1-overview.md … part6-engineering.md
    publish-guide.md
```

## License

CC BY 4.0 — use and adapt with attribution.
