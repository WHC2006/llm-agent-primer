# Part 5: Multi-Agent Systems

[:cn: 中文详述](../多Agent系统.md)

---

- **When:** Complex tasks with distinct roles (e.g. researcher, writer, reviewer); need clear division of labor.
- **Coordination:** Sequential (pipeline), parallel (independent subtasks), debate (multiple views then synthesize), routing (orchestrator picks next agent).
- **Messages:** Sender, role, content; shared state via a shared context or message queue.
- **Multi-agent vs single agent:** Use multiple agents when roles and constraints differ strongly; otherwise one agent with more tools may be enough.
