# Memory and RAG

---

## Is short-term memory the same as “conversation history”? How to manage context?

**Q:** What is short-term memory? Is it the same as conversation history? How do you manage and truncate the context window?

- **Short-term memory:** What the Agent/model can “remember” in the current session—usually **conversation history**: what the user said, what the assistant replied, and if there were tool calls, their inputs and outputs. Together they form the “context” for the next reasoning step.
- **How to manage:** The model has a **context length limit** (e.g. 8K, 32K tokens). Exceeding causes errors or platform truncation. So you need a **truncation strategy**: e.g. keep only the last N turns; or keep by token count newest-first, drop or **summarize** the rest and keep one “previous dialogue summary.” That keeps recent detail without blowing the window.

---

## How do long-term memory and RAG relate? What do vector store, embedding, and retrieval do?

**Q:** How do long-term memory and RAG relate? What are the vector store, embedding, and retrieval flow for?

- **Long-term memory:** You want the model to use information “outside the current conversation”—e.g. company docs, knowledge base, past tickets. You usually **don’t** stuff it all in context but **retrieve** on demand and then add it. **RAG (Retrieval-Augmented Generation)** = augment the current prompt with retrieved content, then have the LLM generate the answer; that’s one way to implement long-term memory.
- **Vector store:** Turn text chunks into **vectors (embeddings)** and store them; at query time turn the “user question” into a vector and use **similarity** (e.g. cosine) to find the most relevant chunks. The vector store stores and looks up these vectors.
- **Embedding:** An embedding model maps text to fixed-length vectors; semantically similar text has similar vectors, so you can “find by meaning.”
- **Retrieval flow:** User question → embed to get query vector → similarity search in the vector store (e.g. Top-K) → get K source chunks → concatenate into the prompt for the LLM. The LLM only sees “question + retrieved chunks” and generates from that.

---

## What are Top-K, rerank, and how to concatenate into the prompt?

**Q:** Retrieval strategies: what are Top-K, rerank, and how to concatenate into the prompt? How to choose K and how to concatenate?

- **Top-K:** In vector retrieval take only the **K most similar** items (e.g. K=5). Too small K can miss relevant docs; too large adds noise, uses tokens, and confuses the model. Often start with 3–10 and tune.
- **Rerank:** First retrieve more candidates (e.g. 20) with the vector search, then use a **reranker model** to score “query + each candidate,” take Top-N (e.g. 5) and put those in the prompt. Rerank is more accurate but slower and costlier; use when accuracy matters.
- **Concatenation:** Join retrieved chunks in order (or as a list) in the system or user message and label clearly “The following is reference; answer only from this” to reduce hallucination. If very long, summarize first or only include the most relevant chunks.

---

## How to combine RAG with Agent? When to retrieve, how to give results to the LLM?

**Q:** Can you combine RAG with an Agent? When to retrieve and how to pass results to the LLM?

- **When to retrieve:** You can **retrieve once after the user asks, before the first LLM call**, and put results in the first prompt; or let the Agent **decide**—in the prompt say “if you need the knowledge base, call the retrieval tool,” and the model issues a “query knowledge base” tool call; then you put retrieval results back as the observation. The first is simple and fixed; the second is more flexible but adds a decision step.
- **How to give results to the LLM:** Put retrieval results as **text** in messages (e.g. as tool content or a “Reference: …” block in user). In the prompt say “Answer only from the reference below; if you can’t, say so.” That helps reduce hallucination.
- **Combination:** RAG supplies “long-term memory” content; the Agent decides when to look up what and combines tool results with RAG results in its reasoning. See Agent architecture.

---

## How to persist memory across turns? How to keep consistency?

**Q:** How do you understand persistence and consistency of memory across multi-turn sessions?

- **Persistence:** For short-term memory (conversation history) to last across sessions you must **store it yourself**: save each turn (user/assistant/tool) by session_id and load it back into context when the user returns. Long-term memory (RAG) is persistent in the vector store; once written, later sessions can query it.
- **Consistency:** If context is truncated or summarized across turns, you can **lose** earlier detail and the model “forgets” what was said, leading to contradiction. Mitigate by: when truncating, keep turns that are relevant to the current question; or summarize older dialogue and keep a “previous agreements/conclusions” summary in context so the model still “knows” key prior conclusions.
