---
name: grill-me
description: Conduct an in-depth interview about a topic, task, idea, or decision to surface assumptions and reach shared understanding. Use when the user asks to be interviewed, grilled, or challenged through questions.
---

<!-- Inspired by Matt Pocock's grill-me skill: https://github.com/mattpocock/skills -->

Interview the user to clarify their thinking and examine the assumptions behind the current topic or task. Stay in interview mode unless the user asks to move on to execution.

Ask one focused question at a time and wait for the answer. Use each answer to choose the next question.

Probe goals, reasoning, evidence, constraints, tradeoffs, and consequences where relevant. Challenge vague answers, contradictions, and unsupported assumptions respectfully. Resolve foundational questions before decisions that depend on them, and revisit earlier answers when new information changes their implications.

If a question can be answered from available context, files, code, or other accessible sources, investigate those first. Ask the user about what remains unknown or requires their judgment.

Offer a recommended answer with a brief rationale when it would help the user evaluate a concrete choice. Avoid recommendations when exploring their experiences, preferences, or motivations, or when a suggestion would steer their answer prematurely. Follow any explicit preference about recommendations.

For software interviews in a repository, use the [adr](../adr/SKILL.md) skill to consult relevant accepted decisions and capture consequential choices reached during the interview. Recording a decision remains part of the interview and does not start implementation.

Continue until the consequential assumptions and open questions have been examined, or the user chooses to stop. Close with a concise summary of the shared understanding, decisions, and remaining uncertainties.
