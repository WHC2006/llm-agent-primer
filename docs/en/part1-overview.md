# Part 1: AI Application Basics

[:cn: 中文详述](../AI应用概览.md)

---

- **App types:** Chatbot (open dialogue), Assistant (task-focused), Copilot (in-tool suggestions), Workflow automation (multi-step, triggered).
- **Stack:** Model layer (OpenAI/Claude/etc.), orchestration (LangChain, LlamaIndex), prompts, RAG (vector DB + embedding), tools, deployment.
- **Boundary:** Pure LLM when the answer fits “model + current input”; add tools/RAG when you need real-time data, exact computation, or side effects (APIs, DB).
