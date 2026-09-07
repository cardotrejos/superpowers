---
name: writing-plans
description: Turn an agreed design or requirements into an implementation plan when the user requests a plan or dependencies, ownership, and verification boundaries need to be coordinated.
---

# Writing Plans

Write a plan that gives an implementer the context and acceptance criteria needed to make sound decisions. Reuse the agreed specification and existing contracts instead of producing a second copy of the implementation.

## Scope and Delivery

For a clear bounded change, an in-task plan may be enough. Save a durable plan when requested or when the work needs a shared record. The default location is `docs/superpowers/plans/YYYY-MM-DD-<feature-name>.md`; user and repository preferences override it.

Use the existing checkout or an isolated worktree according to the task and repository workflow. Planning alone does not require creating a worktree or changing branches.

If the user asked for a plan only, deliver it and stop. If implementation is already authorized, continue after planning unless the user requested a checkpoint or a material constraint requires their decision.

## Define Coherent Units

Map the relevant files, interfaces, dependencies, and established patterns. Split work by independently understandable outcomes and testable boundaries, rather than by a fixed number of minutes, functions, or files.

An interface migration may need several files in one verification unit. Name any temporary breakage allowed inside the unit and the checks that must pass before it is complete. Avoid unrelated restructuring.

Each unit should identify:

- The observable outcome and owned files or interfaces.
- Invariants to preserve and explicit changes to the contract.
- Dependencies and coordination boundaries, including shared mutable state.
- Acceptance evidence and relevant repository-required checks.
- Any unresolved decision or prerequisite that could block the outcome.

## Suggested Plan Shape

```markdown
# [Feature Name] Implementation Plan

**Goal:** [Observable result and scope]
**Approach:** [Chosen design and material tradeoff]
**Constraints:** [Contracts, compatibility, and permission boundaries]
**Spec:** [Link to the agreed design, if one exists]

**Global requirements:** [Relevant version floors, dependency limits, naming/copy rules, and platform constraints with exact values]

### Unit 1: [Outcome]

- Owned files/interfaces: [Verified paths and symbols]
- Interface contract: [Inputs from earlier units and outputs later units depend on; link to authoritative signatures]
- Behavior: [What changes and what must remain true]
- Dependencies: [Prerequisites or independent units]
- Acceptance: [Relevant command or interaction and expected result]
```

Include exact code only when syntax or a fragile integration materially constrains the implementation. Link to existing types, specifications, and examples rather than repeating them. Name concrete error cases and expected behavior; avoid vague instructions such as “add appropriate validation.”

Use existing test commands where possible. Include a failing-behavior check for a practical regression test, and the smallest relevant validation for configuration, generated output, or UI changes. Follow explicit user TDD requirements and repository-required checks.

## Self-Review

Check that each requirement has an owner and acceptance evidence, dependencies are ordered, interfaces agree, and the plan fits the authorized scope. Fix contradictions and placeholders. Mark a genuinely unresolved decision clearly rather than inventing a precise implementation to hide it.

## Execution

Continue with already authorized work. Choose local execution or bounded parallel delegation based on independent work, shared state, and available tools. Use subagent-driven-development or executing-plans when those workflows add value; do not require either merely because a plan exists.

Ask the user to choose an execution method only when they requested that checkpoint or the choice changes a material constraint such as cost, environment, scope, or an external action. A routine method selection is not a reason to pause an implementation request.
