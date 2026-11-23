# AI Engineering Standard

A tool-independent engineering playbook for AI coding agents working across Spring Boot,
React, Angular, and other technology stacks.

## Goals

- Preserve one canonical set of engineering principles across AI tools.
- Make the agent an active engineering partner that challenges weak decisions.
- Support both greenfield development and legacy-system evolution.
- Allow routine in-scope implementation autonomously while gating consequential decisions.
- Explain significant decisions and trade-offs rather than encouraging memorization.
- Verify code with real tests and tools instead of relying on prompt-only assurances.

## v1.0.0 scope

This release establishes the technology-independent foundation:
- Engineering principles and hard boundaries.
- Architecture governance and decision-making.
- Interaction, architecture, and implementation workflows.
- Approval policy.
- Quality governance.
- ADR and technical-design templates.
- Claude Code and Gemini CLI adapter entry points.

Technology-specific standards for Spring Boot, React, and Angular belong to later phases.

## Repository layout

```text
AGENTS.md
README.md
adapters/
  claude-code/
    CLAUDE.md
  gemini/
    GEMINI.md
  chatgpt-codex/
    CHATGPT.md
docs/engineering/
  principles.md
  architecture-governance.md
  decision-making.md
  quality-governance.md
  review-checklist.md
  workflow/
    interaction-protocol.md
    architecture-mode.md
    implementation-mode.md
    approval-policy.md
    project-modes.md
    greenfield-quickstart.md
    scenarios.md
    project-context-template.md
  templates/
    adr-template.md
    technical-design-template.md
```

## Source of truth

`AGENTS.md` is the concise entry point. Detailed standards live under `docs/engineering/`.
Tool-specific files should only explain how a tool discovers and applies the canonical
standard. Avoid duplicating rules across adapters.

Not every AI tool automatically discovers `AGENTS.md`. Verify each tool's context-loading
behavior and configure its adapter accordingly.

## How to use

1. Place this repository at the root of a project, or copy the standard into the project.
2. Ensure the selected AI tool loads the appropriate adapter and `AGENTS.md`.
3. Ask the agent to inspect the repository and identify relevant standards before changing it.
4. Agree on scope and plan.
5. Let the agent implement routine work; approve gated decisions explicitly.
6. Review the completion report and independently enforce deterministic checks in CI.

## Governance profile

- Challenge: always, respectfully and with evidence.
- Project lifecycle: greenfield and legacy.
- ADRs: significant decisions only.
- Principles: hybrid; security and critical boundaries are hard requirements, other
  principles are applied contextually.
- User communication: Turkish by default.
- Standards and technical artifacts: English by default.

## Versioning

Use semantic versioning:
- MAJOR: incompatible changes to the standard's behavioral contract.
- MINOR: backward-compatible principles, workflows, or capabilities.
- PATCH: clarifications and corrections that do not change intended behavior.

## Important limitation

A prompt or instruction file cannot guarantee compliance. Enforce deterministic requirements
with repository tooling, tests, linters, architecture tests, security scanners, and CI.
Treat agent self-review as a useful additional layer, not the sole quality gate.
