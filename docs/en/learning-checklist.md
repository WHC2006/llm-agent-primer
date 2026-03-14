# Learning Checklist — AI Applications & Agents

[:cn: 中文版](../学习清单-AI应用与Agent.md)

---

## How to Use

- Use this as the **syllabus**: follow Part 1 → Part 6; check off items as you go.
- Full Q&A content is in the **Chinese notes** (see sidebar); this page is a concise EN checklist.

---

## Part 1: AI Application Basics

- [ ] Distinguish app types: chatbot, assistant, Copilot, workflow automation
- [ ] Know the stack: LLM API, prompts, context, tokens
- [ ] Understand when to use pure LLM vs tools / external data
- [ ] Be able to build a minimal single- or multi-turn chat app

---

## Part 2: LLM & Prompt Engineering

- [ ] Understand LLM capabilities, limits, and when to add an Agent
- [ ] Use role, task, format, few-shot in prompts
- [ ] Manage context window, long text, token cost and latency
- [ ] Choose models by capability, cost, latency
- [ ] Handle hallucination, repetition, format drift

---

## Part 3: Agent Core

- [ ] Understand Agent loop: perceive → reason → act → feedback
- [ ] Use ReAct (thought–action–observation) and Plan-and-Execute
- [ ] Understand Tool Use / Function Calling
- [ ] Know CoT, ReAct, Reflection; define and call tools; tool design and safety

---

## Part 4: Memory & RAG

- [ ] Short-term memory: conversation history, context and truncation
- [ ] Long-term memory and RAG: vector store, embedding, retrieval
- [ ] Retrieval strategies: Top-K, rerank, how to inject into the prompt
- [ ] Combine RAG with Agent; persistence and multi-turn consistency

---

## Part 5: Multi-Agent

- [ ] When to use multiple agents; roles (e.g. researcher, coder, reviewer)
- [ ] Coordination: sequential, parallel, debate, routing
- [ ] Message format and shared state
- [ ] When multi-agent vs single agent with more tools
- [ ] Frameworks: Crew, Team, Role concepts

---

## Part 6: Engineering & Production

- [ ] Framework choice: LangChain, LlamaIndex, CrewAI, AutoGen
- [ ] Evaluate: hallucination, latency, cost, observability
- [ ] Logging, tracing, monitoring
- [ ] Security and compliance: filtering, permissions, privacy
- [ ] Deployment: API, async jobs, integration with existing systems

---

## Appendix

- Official docs, papers (ReAct, Toolformer, RAG), open-source repos, communities.
