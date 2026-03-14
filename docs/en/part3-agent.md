# Part 3: Agent Core

[:cn: 架构](../Agent架构.md) · [:cn: 工具](../工具与Function-Calling.md)

---

- **Loop:** Perceive (context) → Reason (LLM decides next step) → Act (run tools) → Feedback (results back into context); repeat until final answer.
- **ReAct:** Thought → Action (tool + args) → Observation (tool result); when next step depends on previous result.
- **Plan-and-Execute:** Plan steps first, then execute in order; good when steps are clear.
- **Tools:** Define name, description, params (e.g. JSON Schema); model returns tool_calls; you execute and append results. Design: one concern per tool, clear descriptions, safety and permissions.
