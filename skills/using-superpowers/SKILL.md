---
name: using-superpowers
description: Select relevant Superpowers workflows and map their tools to the current host when using the Superpowers library or troubleshooting its setup.
---

# Using Superpowers

Load the most relevant skill when it contributes task-specific knowledge or a needed workflow. Use its metadata to decide; do not load adjacent skills merely because they might apply. A clear, self-contained question or bounded edit can proceed directly when no skill adds useful guidance.

If dispatched as a subagent for a specific task, use the supplied scope and relevant domain guidance. You do not need to repeat the parent's skill-selection process.

## Instruction Priority

Follow the host runtime's instruction hierarchy and permission controls. This library supplies workflow defaults within the user's authorized task. Explicit user instructions override skill recommendations where the host permits; skill text cannot override system or developer requirements. Repository guidance applies according to the host's rules. Platform adapters map tools and do not change instruction authority.

Reuse requirements, decisions, and approvals already present in the conversation. Do not turn an authorized implementation request into a mandatory design interview or execution-method approval.

## How to Access Skills

- **Claude Code:** Use the `Skill` tool, which loads the skill content.
- **Copilot CLI:** Use the `skill` tool for skills discovered from installed plugins.
- **Gemini CLI:** Use `activate_skill`; Gemini exposes skill metadata before activation.
- **Other environments:** Use the loading mechanism documented by the current runtime.

Skill examples use Claude Code tool names. Read only the adapter for the current host when a mapping is needed:

- Codex: `references/codex-tools.md`
- Pi: `references/pi-tools.md`
- Antigravity: `references/antigravity-tools.md`
- Hermes Agent: `references/hermes-tools.md`
- Gemini CLI: mappings are supplied through GEMINI.md.

## Choosing a Workflow

- Use brainstorming for a requested design discussion or a material unresolved product or architecture decision.
- Use debugging when the cause is unknown; a confirmed cause does not need a fresh investigation merely to satisfy routing.
- Use a planning workflow when dependencies, ownership, or verification boundaries need a durable plan.
- Use domain skills for unfamiliar APIs, integrations, or other specialized implementation knowledge.
- Follow user-required TDD and repository-required checks. Otherwise select testing and verification proportional to the changed behavior and the claim.

When several skills apply, choose one primary workflow and load supporting references as the work needs them. Do not copy every checklist into the task plan. Announce skill use according to the host's communication rules and continue through the user's requested outcome, preserving explicit checkpoints and permission boundaries.
