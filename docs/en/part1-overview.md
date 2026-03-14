# AI Application Overview

---

## How to distinguish common application types

**Q:** How do you distinguish common application types?

You can distinguish along three dimensions: **interaction style**, **whether tools/external data are used**, and **relationship to the business system**.

### By interaction style

| Type | Typical interaction | Examples |
|------|---------------------|----------|
| Chatbot | Multi-turn, Q&A, open-ended | Customer support, chitchat, simple advice |
| Assistant | Multi-turn with clear tasks (email, summarization, translation) | Personal assistant, writing/translation helper |
| Copilot | In-context in a tool: completions, suggestions, explaining current content | Code completion, document suggestions, spreadsheet formulas |
| Workflow automation (Workflow / Agent) | User gives a goal or trigger; system runs multiple steps, may call tools | Scheduled reports, auto booking, cross-system data handling |

### By use of tools / external data

- **Pure dialogue:** Only LLM + context; no API calls, no DB. Good for chitchat, light writing, translation, knowledge Q&A.
- **Dialogue with tools:** Calls search, calculator, DB, APIs, etc. Good when you need live data, exact computation, or to act on external systems.
- **Automation pipeline:** Event- or time-triggered; runs steps (LLM decisions + tool calls). Good for background jobs, batch work, integration with existing systems.

### By relationship to the business system

- **Standalone app:** Separate product/page; user comes to chat or give commands.
- **Embedded (Copilot):** Inside IDE, Office, internal systems; suggests or acts on current document/code/data.
- **Background (Agent/automation):** User sets goal or rules; system runs in the background; results via notifications/reports/tickets.

### One-line summary

- **Chatbot:** Multi-turn, open, companion/advice; can be pure LLM.
- **Assistant:** Multi-turn + clear task; often needs tools.
- **Copilot:** Inside a tool; completes, suggests, or explains “current content.”
- **Workflow/Agent automation:** User gives goal or trigger; system runs multiple steps (may use tools); dialogue is optional.

---

## Typical tech stack and representative products

**Q:** What is the typical tech stack, and what are representative products?

Think in layers; each has common representatives.

### 1. Model layer (LLM)

Provides the “brain”: understanding, generation, reasoning.

| Type | Representatives |
|------|-----------------|
| Closed-source API | OpenAI (GPT-4o / GPT-4), Anthropic (Claude), Google (Gemini) |
| Regional commercial | Various local providers |
| Open-source | Llama, Qwen, DeepSeek, Mistral, etc. |

### 2. Access and orchestration layer

Calls model APIs, assembles prompts, manages turns and tool calls.

| Type | Representatives |
|------|-----------------|
| Frameworks/SDKs | LangChain, LlamaIndex, Semantic Kernel, CrewAI, AutoGen |
| Direct calls | Official SDKs (openai, anthropic, etc.) |

### 3. Prompts and context

Design system/user prompts; manage context window and tokens. Usually done in framework or custom code; no separate “product”; can use template engines or PromptLayer.

### 4. Memory and retrieval (RAG)

Long-term memory, knowledge base, retrieval-augmented generation.

| Component | Representatives |
|-----------|-----------------|
| Vector store | Pinecone, Weaviate, Milvus, Chroma, pgvector |
| Embedding models | OpenAI Embeddings, Cohere, open-source sentence-transformers |
| Assembly | Often via LangChain / LlamaIndex with the LLM |

### 5. Tools and external capabilities

Search, computation, APIs, code execution, etc.

| Type | Representatives |
|------|-----------------|
| Search | Bing/Google API, Serper, etc. |
| Code execution | E2B, Sandbox, etc. |
| Other | Your own or third-party APIs |

### 6. Deployment and operations

Hosting, auth, rate limiting, monitoring and evaluation.

| Type | Representatives |
|------|-----------------|
| Hosting | Vercel, Cloudflare Workers, your own backend + model API |
| Observability | LangSmith, Langfuse, etc. |

### Stack sketch

```
Front end / trigger → Orchestration (e.g. LangChain) → LLM API + prompts/context
    → optional (vector store + embedding, tool APIs) → business logic and storage
```

“Representative products” are usually combinations: e.g. **OpenAI API + LangChain + Pinecone** is one common stack; **ChatGPT, GitHub Copilot, Notion AI** are end products built on such stacks.

---

## Pure LLM dialogue vs. needing tools/external data

**Q:** How do you understand the boundary between “pure LLM dialogue” and “needs tools/external data”?

### Definitions

- **Pure LLM dialogue:** Only “model + text you give it (including multi-turn history)” to generate a reply; no external APIs, no DB, no code execution. Input and output are text; the model only “continues from the current context.”
- **Needs tools/external data:** During the dialogue the system calls search, calculator, DB, API, code execution, etc., and puts “external results” back into context so the model can reason or generate from them.

### Where to draw the line

**When pure LLM is enough:**

- Does not depend on “right-now” information (e.g. today’s weather, stock price, news).
- No need for exact computation, lookups, or your private data.
- No need to “do things” (send email, update DB, call API).

Typical: chitchat, light editing, translation, explaining concepts from model knowledge, generating structure (outline, template).

**When you need tools/external data:**

- **Live/accurate facts:** weather, stock price, latest docs, knowledge base.
- **Exact computation or retrieval:** math, lookups, finding answers in many documents (RAG).
- **Side effects:** send email, create ticket, update data, call business API.

Typical: search-backed Q&A, personal/enterprise knowledge-base Q&A, booking, code execution, reports from real data.

### One-line summary

If the task only needs “what the model already learned + what’s already in the conversation,” use pure LLM. If it needs “live/external/private data” or “acting in the system,” add tools or external data—that’s when you move into Agent/tool-augmented setups.
