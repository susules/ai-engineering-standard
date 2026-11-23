# Contributing

Thank you for considering a contribution to AI Engineering Standard.

## Guiding Principle

This repository is a living engineering standard, not a collection of opinions.
Every change must improve clarity, correctness, or practical usefulness.
Avoid adding rules that cannot be justified with evidence or reasoning.

## What Belongs Here

- Corrections to factually wrong or misleading content.
- Clarifications that remove ambiguity without changing intent.
- New principles, workflows, or patterns that are technology-independent and justified.
- New technology-specific standards (Spring Boot, React, Angular, etc.) in `docs/stacks/`.
- New behavior evaluation scenarios in `scenarios.md`.
- Adapter improvements for Claude Code, Gemini, or ChatGPT/Codex.

## What Does Not Belong Here

- Opinions without engineering rationale.
- Technology-specific rules in technology-independent documents.
- Duplicating content that already exists in `AGENTS.md` or `docs/engineering/`.
- Prescribing a specific architecture style as a universal default.

## How to Contribute

1. Open an issue describing the problem or gap before writing content.
2. Fork the repository and create a branch: `fix/description` or `feat/description`.
3. Make focused changes. One concern per pull request.
4. Update `CHANGELOG.md` under an `[Unreleased]` section.
5. If the change affects agent behavior, add or update a scenario in `scenarios.md`.
6. Submit a pull request with a clear description of what changed and why.

## Versioning

Follow the versioning guide in `CHANGELOG.md`:
- **MAJOR**: behavioral contract change.
- **MINOR**: new backward-compatible content.
- **PATCH**: clarification or correction.

## Language

- Contribution discussions and pull request descriptions: English or Turkish.
- All standard documents, code, and technical artifacts: English.
- `kullanımKlavuzu.md`: Turkish only.

## License

By contributing, you agree that your contributions are licensed under the
Apache License 2.0 as described in `LICENSE`.
