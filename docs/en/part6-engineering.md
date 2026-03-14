# Agent Engineering and Production

---

## What are LangChain, LlamaIndex, CrewAI, AutoGen for? How to choose?

**Q:** What are these frameworks for and how do you choose?

- **LangChain:** **General orchestration.** Abstracts LLM calls, prompt templates, tools, chained steps, memory, RAG into components and wires them with “chains” or LCEL. Good for highly custom Agents or pipelines with mixed data sources and tools. Large ecosystem and docs, but many abstractions and a learning curve.
- **LlamaIndex:** **Data and retrieval.** Good at turning data sources (docs, APIs, DBs) into indexes and RAG queries, then connecting to the LLM. Good for “retrieval/knowledge-base-first” apps; Agent logic can be custom or combined with LangChain.
- **CrewAI:** **Multi-agent collaboration.** Role, Task, Crew abstractions to form a team of Agents that work in sequence or by flow. Good for clear “multi-role” scripted tasks (e.g. research → write → review).
- **AutoGen:** Microsoft’s **multi-agent dialogue** framework. Multiple Agents can message each other; human-in-the-loop is supported. Good for conversational collaboration, debate, and when humans need to step in.

**How to choose:** If you mainly do RAG + simple Agent, LlamaIndex + a bit of custom logic may be enough. If single Agent with many tools and complex chains, use LangChain. If you have a clear multi-role script, use CrewAI or AutoGen. You can also mix (e.g. LlamaIndex for retrieval, LangChain for Agent orchestration).

---

## What dimensions matter for evaluating Agents? Hallucination, latency, cost?

**Q:** How do you handle evaluation: hallucination, latency, cost, stability, observability?

- **Hallucination:** Model produces content that doesn’t match facts or given context. You can sample and label “hallucination or not”; or use rules/models to check consistency (e.g. in RAG: can key facts in the answer be found in retrieved chunks?). Reduce with better prompts, RAG constraints, output checks, or Reflection.
- **Latency:** Time from user request to final reply. Look at P50/P99 and “time to first token” (for streaming). For multi-step Agents, sum each LLM + tool call; optimize by faster model, less context, parallel tool calls, caching.
- **Cost:** With per-token pricing, track prompt_tokens and completion_tokens per request/user and multiply by rate. Set per-user or per-day caps and alert. Optimize by model choice, shorter prompts, truncating history, caching repeated prefix.
- **Stability and observability:** Success rate, error types (timeout, rate limit, format errors); log key steps and report traces (e.g. LangSmith, Langfuse) to see “which step failed and what the model returned.”

---

## How are logging, tracing, and monitoring used in debugging and ops?

**Q:** What’s the role of logging, tracing, and monitoring in Agent debugging and ops?

- **Logging:** Per request log “input summary, which tools were called, tool return summary, final output, token usage, errors.” Helps later debug “what the user said, what the model chose, whether the result was correct.”
- **Tracing:** Break one user request into **multiple spans** (e.g. LLM call 1, tool A, LLM call 2, tool B, LLM call 3) and record input/output and duration for each. That shows where latency and cost come from and helps optimization and debugging.
- **Monitoring:** **Aggregate and alert** on latency, error rate, token usage, cost (e.g. P99 &gt; 10s, daily cost over threshold). Use logs and traces for debugging; use monitoring to detect issues in production and drill into specific request traces.

---

## What about security and compliance? Input/output filtering, permissions, privacy?

**Q:** What to consider for security and compliance: input/output filtering, permissions, data privacy, audit?

- **Input filtering:** Length limits, sensitive/forbidden term filters, simple injection detection (e.g. “ignore above instructions”-style patterns) to reduce prompt injection and abuse.
- **Output filtering:** Sanitize model output (e.g. mask phone numbers, IDs); forbid output of internal prompt or system info; if output is shown directly to users, add a policy check.
- **Permissions:** Tools and data with **least privilege** (who can use what). E.g. delete data, send email only for authorized Agents or with confirmation; RAG retrieval can be isolated by user/tenant.
- **Data privacy and audit:** Be clear what data goes to the LLM (including third-party APIs) and whether that matches privacy policy; keep **audit logs** for sensitive actions (who, when, what was called, result summary) for compliance and investigation.

---

## What deployment options exist? How to integrate with existing systems?

**Q:** Common deployment patterns: API service, async tasks, integration with existing systems?

- **API service:** Expose the Agent as an HTTP/gRPC API for the front end or other services. Synchronous: “request → multi-step reasoning and tools → return final reply”; if timeouts are a risk, use “submit task → poll or callback for result.”
- **Async tasks:** User requests go to a queue; workers run the Agent and write results to storage or send notifications. Good when delay is acceptable (report generation, batch jobs); can use existing queues (Celery, SQS, etc.).
- **Integration with existing systems:** The Agent runs as an internal service called by existing business logic (e.g. “smart reply” button in support UI); or the Agent calls existing APIs/DBs via tools. Pay attention to auth, rate limits, error codes, and retry policy consistency.
