---
name: brainstorming
description: Clarify and compare designs when the user asks to brainstorm or an unresolved product or architecture decision would materially change implementation.
---

# Brainstorming Ideas Into Designs

Turn open questions into a concrete design that can guide implementation. Reuse the requirements, decisions, and approvals already present in the task.

## Choose the Necessary Depth

For a clear, bounded request, record necessary assumptions and proceed with the authorized work. A config change or single-function utility does not automatically need an interview, alternatives, or a separate specification.

Choose a path based on the deliverable:

- **Spike:** A feasibility question whose deliverable is evidence and a recommendation. Keep any prototype clearly labeled as throwaway; retaining it as product code needs implementation scope.
- **Bounded:** A well-scoped change with a clear approach. A short in-chat design or task plan is enough; it need not create a spec file or implementation plan document.
- **Architectural:** A new subsystem or a material change to component relationships or shared interfaces. Record contracts and dependencies in a durable design when needed.

Reassess the path when new evidence changes the scope. Add process for a material unresolved decision, and remove unnecessary process when the existing contracts settle it.

For a material unresolved decision, first inspect the relevant code, constraints, and existing design records. Resolve observable questions from evidence or a small reversible experiment. Ask the user about intent or preferences only when the answer would change the implementation and cannot be inferred reliably.

If the user requested brainstorming or a plan only, deliver that artifact and stop at that scope. If the user requested implementation, continue after resolving the design unless they requested a checkpoint or the next action needs additional authority.

## Explore the Design

- Anchor the discussion in purpose, constraints, and observable success criteria.
- Offer alternatives when more than one credible approach remains. Explain the tradeoffs and recommend one; do not invent alternatives to fill a quota.
- Make any decision requiring the user's input concrete and reviewable before asking. Keep questions focused and avoid repeating settled decisions.
- Scale the design to the work. Include architecture, data flow, error handling, and testing where they affect a decision.
- Decompose a large request into coherent units with clear dependencies and acceptance evidence. Work on independent authorized units while a material question remains open.

## Design for Isolation and Clarity

Give each unit a clear purpose, interface, and set of dependencies. Prefer boundaries that let a reader understand a caller without reading every implementation detail, and let tests exercise behavior without excessive setup.

In existing codebases, inspect the current structure and follow established patterns. Include targeted structural improvements only where they serve the requested change. Keep unrelated refactoring out of the design.

## Record and Review

Use a written specification when the work needs a durable design, multiple implementers need a shared contract, or the user requests one. The default location is `docs/superpowers/specs/YYYY-MM-DD-<topic>-design.md`; repository or user preferences override it. Small designs can stay in the task's plan or response.

Review the design for missing requirements, contradictory assumptions, ambiguous contracts, and unnecessary scope. Resolve issues supported by the existing request directly. Mark a genuinely unresolved decision rather than silently guessing.

Do not require a second approval for an unchanged design already approved in this conversation. Ask again only if a material change invalidates the earlier decision or the user explicitly requested review of the saved document. Commit documents according to the task's existing Git scope and repository workflow.

## Continue to Implementation

Use writing-plans when the agreed design needs a separate implementation plan. A small, clear change can proceed directly with the relevant implementation guidance. Complete the already authorized work rather than stopping to ask which workflow to use.

## Visual Companion

Use visual mockups or diagrams when seeing the alternatives will help resolve the design. Use the host's available visual tools and permission rules. Do not make acceptance of an optional visualization a prerequisite for unrelated progress.

The bundled browser companion is optional. Offer it only when a specific question would be clearer shown than described. If useful and allowed in the task, read [visual-companion.md](visual-companion.md) for its setup, security, and lifecycle requirements. When the user accepts opening it, start the server with `--open` so the browser reaches the first screen. If declined, continue in text and do not offer again unless requested. Use it for visual content such as layouts or side-by-side designs; keep textual requirements and tradeoffs in the conversation.
