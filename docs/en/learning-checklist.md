# Learning Checklist — AI Applications & Agents

---

## How to Use

> [!info] Usage
> - This checklist is the **syllabus**: Part 1 → Part 6 in order works best; you can skip around if needed.
> - Use the `- [ ]` items in Obsidian to track progress.
> - Modules with `[[note name]]` can be separate notes; add links to build a bidirectional knowledge base.
> - Concrete knowledge is built by Q&A in the corresponding notes; this file only lists *what* to learn.

---

## Part 1: AI Application Basics

See: [Part 1 – AI overview](part1-overview.md)

- [ ] Distinguish common AI app types: chatbot, assistant, workflow automation, Copilot, etc.
- [ ] Understand the typical stack: LLM API, prompt engineering, context and tokens
- [ ] Understand the boundary between “pure LLM dialogue” and “needs tools/external data”
- [ ] Know how to build a minimal AI chat app from scratch (single- or multi-turn)

---

## Part 2: Large Language Models (LLM)

See: [Part 2 – LLM](part2-llm.md)

- [ ] Understand LLM capabilities and limits, and when to introduce an Agent vs. single call
- [ ] Master prompt-engineering basics: role, task, output format, few-shot examples
- [ ] Understand context window, long text, token usage, and cost vs. latency tradeoffs
- [ ] Choose the right model by scenario (capability, price, latency)
- [ ] Know common issues: hallucination, repetition, format drift and how to handle them

---

## Part 3: Agent Core

### 3.1 Architecture and paradigms

See: [Part 3 – Agent](part3-agent.md)

- [ ] Understand Agent loop: perceive → reason → act → feedback
- [ ] Master ReAct: thought–action–observation cycle and when to use it
- [ ] Master Plan-and-Execute: plan steps first, then execute; when to use it
- [ ] Understand the role of Tool Use / Function Calling in Agents

### 3.2 Reasoning and tools

See: [Part 3 – Tools](part3-agent.md)

- [ ] Know reasoning styles: CoT, ReAct, Reflection
- [ ] Define and call a tool with Function Calling (e.g. search, calculator)
- [ ] Understand how tool description (name, params, description) affects model choice and calls
- [ ] Know tool design: when to split tools, granularity, safety and permissions

---

## Part 4: Memory and Retrieval

See: [Part 4 – RAG](part4-rag.md)

- [ ] Short-term memory: conversation history, context window and truncation
- [ ] Long-term memory and RAG: vector store, embedding, retrieval flow
- [ ] Retrieval strategies: Top-K, rerank, how to inject into the prompt
- [ ] Combine RAG with Agent: when to retrieve, how to pass results to the LLM
- [ ] Persistence and consistency across multi-turn sessions

---

## Part 5: Multi-Agent and Collaboration

See: [Part 5 – Multi-Agent](part5-multiagent.md)

- [ ] Typical multi-agent scenarios and role split (e.g. researcher, coder, reviewer)
- [ ] Coordination: sequential, parallel, debate, routing/scheduling
- [ ] Message format and shared state between agents
- [ ] When to use multi-agent vs. single agent with more tools
- [ ] Common abstractions: Crew, Team, Role

---

## Part 6: Engineering and Production

See: [Part 6 – Engineering](part6-engineering.md)

- [ ] Framework choice: LangChain, LlamaIndex, CrewAI, AutoGen, etc.
- [ ] Evaluation: hallucination, latency, cost, stability, observability
- [ ] Logging, tracing, monitoring for debugging and ops
- [ ] Security and compliance: input/output filtering, permissions, data privacy, audit
- [ ] Deployment: API service, async jobs, integration with existing systems

---

## Appendix: Recommended resources

> [!tip] Placeholder
> To be filled; you can add separate notes and link them here.

- Official docs and tutorials (by framework/model you use)
- Key papers (e.g. ReAct, Toolformer, RAG)
- Open-source projects and example repos (by topic)
- Communities and blogs (ongoing)
