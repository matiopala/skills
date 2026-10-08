---
name: deliver
description: Guide a software change through requirements interviewing, focused research, planning, implementation, and acceptance verification. Use when the user requests this development workflow.
---

<!-- Inspired by Matt Pocock's grill-me and HumanLayer's research-plan-implement workflow:
https://github.com/mattpocock/skills
https://github.com/humanlayer/humanlayer/tree/main/.claude/commands
-->

Follow the stages covered by the user's request and existing authorization.
Resume from established decisions and completed work.

## Task records

When working from a task file or tracker issue, read its brief, status, and
relevant linked context. Use it as the authoritative working record. Preserve
the agreed brief and acceptance criteria, and record consequential changes
explicitly.

Add the implementation plan, progress, and verification evidence to that same
record in its existing location. Maintain one authoritative task record;
link to it rather than creating duplicate task or delivery records.

A task record is optional. For standalone requests, work from the available
context and follow the user's requested output format and project conventions.

## 1. Interview

Ask one consequential question at a time. Investigate relevant code and
context around each question before asking the user for information that
inspection could establish.

Clarify the desired outcome, scope, constraints, concrete acceptance
examples, and existing behavior that must remain working. Challenge vague
answers and conflicting assumptions respectfully. Recommend an answer
when it helps resolve a concrete tradeoff.

Finish when these are sufficiently clear to guide research and planning.

## 2. Research

Use the requirements to trace affected behavior, dependencies, boundaries,
existing patterns, and tests. Reuse findings from the interview and verify
assumptions against current code.

Use parallel research for independent questions when useful and available.
Give each investigation a bounded question and reconcile its findings.

Identify regression risks and how the desired outcome can be demonstrated.
Record concise findings with code references. Return to the user when a
discovery changes a consequential requirement or tradeoff.

## 3. Plan

Define the final state in observable terms. Describe the smallest approach
that achieves it, including consequential interface, data, compatibility,
and failure-handling decisions. Use phases when they make work easier to
verify. Leave routine coding details to implementation.

For every goal, define:

- Acceptance scenarios and expected observable results.
- The tests or checks that demonstrate those results.
- The irrefutable proof to collect before claiming delivery.

Define irrefutable proof as reproducible, inspectable evidence that the
acceptance criteria hold under the stated test conditions.

Include regression checks for affected existing functionality. Favor
integration and end-to-end tests that exercise meaningful behavior through
real affected components. Use unit tests where useful; coverage percentage
is not a delivery criterion.

Resolve consequential uncertainties before implementation. Keep the plan
and acceptance checklist available for tracking work and resuming later.

## 4. Implement

Make scoped increments and build acceptance and regression tests alongside
the changes. Establish relevant baseline behavior when useful, and
reproduce reported bugs with a failing test when practical.

Apply these principles:

- Make the smallest correct change that fully achieves the goal and fits
  existing conventions.
- Minimize complexity. Add abstractions, configuration, and infrastructure
  only for concrete needs. Measure before optimizing.
- Give each module one coherent responsibility and a small interface.
  Hide its implementation complexity. Avoid empty forwarding layers.
- Keep boundaries explicit. Validate external data, expose dependencies,
  and use structures that make invalid states difficult to represent.
- Handle meaningful failures deliberately. Handle, translate, retry, or
  propagate them. Make retryable operations idempotent where practical.

Adapt routine implementation details as needed. If findings change scope,
acceptance criteria, or consequential design decisions, update the plan
and resolve the decision with the user. Honor authorization already given.

## 5. Prove delivery

Run the acceptance and relevant regression checks against the final code.
Fix failures introduced by the change. Identify pre-existing failures
separately.

For each acceptance criterion, report the result and supporting evidence:
the scenario or test, how to reproduce it, and what was observed. Identify
the code state tested and any relevant environment limitations or mocks.

Do not weaken acceptance criteria to make the implementation pass.
Distinguish verified behavior from assumptions and unverified checks.
If required evidence is unavailable, report the gap and leave the affected
criterion incomplete.

When using a task record, mark it complete only when the required evidence
supports all acceptance criteria.

Finish with the delivered outcome, acceptance evidence, regression
results, and any remaining limitations.
