# Multi-Agent Systems

---

## What are typical multi-agent scenarios? How to split roles?

**Q:** What are typical multi-agent scenarios and role splits? E.g. researcher, coder, reviewer?

- **Typical scenarios:** When the task is **complex and naturally splits into different capabilities**. E.g. writing an industry report = someone researches, someone drafts, someone reviews; building a feature = someone designs, someone codes, someone tests. A single Agent with many tools can do it too, but multi-agent makes “who does which step” explicit in different roles, which helps division of labor, constraints, and iteration.
- **Role split:** Split by **responsibility**; each Agent has a fixed role (in the system prompt). E.g. **Researcher** only retrieves and summarizes, doesn’t write conclusions; **Writer** drafts from the researcher’s material; **Reviewer** only checks facts and logic and suggests edits. Each Agent’s prompt stays simple and behavior more controllable; you can tune or swap models per role.

---

## What do sequential, parallel, debate, and routing mean?

**Q:** What do the coordination styles—sequential, parallel, debate, routing/scheduling—mean?

- **Sequential:** Agent A finishes and passes to B, B to C, etc.—a pipeline. Good when steps are strongly dependent (research then write then review).
- **Parallel:** Several Agents run at once on different subtasks (e.g. look up three sources in parallel), then results are combined. Good when subtasks are independent; saves time.
- **Debate:** Several Agents each give an answer or position on the same question, then critique and complement each other; finally one Agent or a human synthesizes. Good when you want multiple perspectives and to reduce single-model bias or error.
- **Routing/scheduling:** A **coordinator** (rules or a small model) decides “which Agent next and what input” from user intent or current state. Good when the task has many branches and the path isn’t fixed.

---

## What message format do multi-agents use? How is state shared?

**Q:** How do multi-agents format messages and share state?

- **Message format:** Usually a **uniform structure**, e.g. each message has: sender (agent_id), role, content (text or structured), optional metadata (time, task id). Content can be natural language or JSON like “task description + input data” for the next Agent to parse. Similar to single-Agent user/assistant/tool, but the “sender” is different Agents.
- **State sharing:** You can have a **shared context** (e.g. a shared dict or document) where each Agent reads current state and writes its output; the next Agent reads what it needs. Or use a **message queue**: each Agent only consumes the previous Agent’s output and produces for the next; state is entirely in messages, no shared memory. Choice depends on whether multiple Agents need to read the same intermediate result repeatedly.

---

## When is multi-agent worth it vs. one Agent with more tools?

**Q:** When to use multi-agent instead of one Agent with more tools?

- **Single Agent, many tools:** One model, many tools; the model decides when to use which. Good when **steps aren’t too many and the decision path is relatively clear**; simple to implement, lower latency.
- **Multi-agent:** Good when **there are many steps and each step needs a different “persona” or strong constraint**. E.g. “research first, then write; the writer must not search”—two Agents make that easier to enforce; or you need “multiple agents debate then synthesize,” which one Agent can’t really do. If it’s just “one assistant that can search, compute, and write,” one Agent + many tools is usually enough. Multi-agent adds more calls, more context passing, and coordination logic, so use it when “division of labor clearly pays off.”

---

## What do Crew, Team, Role mean in frameworks?

**Q:** What do the common multi-agent abstractions (Crew, Team, Role) mean?

- **Role:** An Agent’s **identity and responsibility**—usually name, goal, backstory or system prompt, and the tools it can use. E.g. “Researcher” role: goal is to gather and summarize information; only search and read tools.
- **Team / Crew:** A **set** of Agents and how they collaborate. E.g. Crew: a set of Roles that run in sequence or by a graph, with a “manager” assigning tasks or collecting results. Team is similar; in some frameworks it’s “a group of Agents with a shared goal.”
- Frameworks (CrewAI, AutoGen, etc.) differ in wording, but the core is: **Role = who does what**, **Crew/Team = who works with whom how**; in practice often “one LLM config + tool set per Role, Crew does scheduling and messaging.”
