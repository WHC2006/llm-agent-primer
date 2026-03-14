# Part 4: Memory & RAG

[:cn: 中文详述](../记忆与RAG.md)

---

- **Short-term:** Conversation history; manage with truncation or summarization to fit context.
- **Long-term / RAG:** Vector store + embeddings; retrieve by similarity (e.g. Top-K), optionally rerank; paste results into the prompt.
- **With Agent:** Retrieve before first LLM call, or let the Agent request retrieval via a tool; always pass retrieved text explicitly and instruct the model to stick to it.
- **Persistence:** Store conversation by session; keep vector index updated; preserve summaries for consistency across turns.
