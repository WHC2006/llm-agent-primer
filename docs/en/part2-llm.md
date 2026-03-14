# Part 2: LLM & Prompt Engineering

[:cn: 中文详述](../LLM与提示工程.md)

---

- **What LLMs do:** Next-token prediction; “ability” comes from fitting language and knowledge in training. Limits: no external world, no verification → hallucination, staleness, no execution.
- **When to use an Agent:** When you need live/external data, multi-step reasoning, tools, or open-ended tasks.
- **Prompts:** Role, task, format, few-shot; iterate. Risk: prompt injection → isolate structure, validate output, least privilege.
- **Context & cost:** Respect context window; long text → chunk + RAG or summarize; count tokens; trade off model size, context length, streaming, cache.
