# AI 应用与 Agent 学习笔记

围绕 AI 应用、LLM、提示工程、Agent、RAG 与多 Agent 的成体系学习笔记。**双语：** 主体为**中文**；[English 概览](docs/en/index.md) 在 `docs/en/`。文档站侧栏顶部用 **中文** / **English** 链接切换语言。

## 学习路径

内容按六个部分组织，建议从学习清单起按顺序看，再点进各笔记。

| 部分 | 主题 | 主笔记 |
|------|--------|--------|
| 1 | AI 应用基础（形态、技术栈、何时用工具） | [AI应用概览](docs/AI应用概览.md) |
| 2 | LLM 与提示工程（能力边界、提示、上下文与成本） | [LLM与提示工程](docs/LLM与提示工程.md) |
| 3 | Agent 核心（ReAct、Plan-and-Execute、工具与 Function Calling） | [Agent架构](docs/Agent架构.md)、[工具与Function-Calling](docs/工具与Function-Calling.md) |
| 4 | 记忆与 RAG（短期/长期记忆、检索、多轮） | [记忆与RAG](docs/记忆与RAG.md) |
| 5 | 多 Agent（角色、协调、消息） | [多Agent系统](docs/多Agent系统.md) |
| 6 | 工程化与落地（框架、评估、安全、部署） | [Agent工程化](docs/Agent工程化.md) |

**学习清单（总纲）：** [学习清单-AI应用与Agent](docs/学习清单-AI应用与Agent.md)

## 使用方式

- **只读：** 用任意 Markdown 阅读器或 GitHub 打开各 `.md` 即可。
- **带链接：** 用 [Obsidian](https://obsidian.md) 打开本仓库，`[[笔记名]]` 可正常跳转。

## 文件结构

- **仓库根目录：** 本 `README.md`、`mkdocs.yml` 及配置。
- **文档（文档站源码）：** 笔记均在 [`docs/`](docs/) 下，GitHub Pages 由 MkDocs 从 `docs/` 构建。

```
docs/
  index.md                    ← 站点首页（中文）
  学习清单-AI应用与Agent.md   ← 建议从这里开始
  AI应用概览.md
  LLM与提示工程.md
  ...（Part 1～6 笔记）
  发布文档指南.md
  en/                         ← 英文
    index.md                  ← 英文首页
    learning-checklist.md
    part1-overview.md … part6-engineering.md
    publish-guide.md
```

## 许可

CC BY 4.0 — 可转载与演绎，需署名。
