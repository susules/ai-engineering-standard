# PROJECT_CONTEXT.md

Copy to the project root as `PROJECT_CONTEXT.md`. Keep it short and current.
The standard is generic; this file holds everything specific to this project.

## Identity
- Project name:
- Purpose (one sentence):
- Standard version in use (see AGENTS.md):

## Mode
- Mode: greenfield | legacy | migration
- Per-area modes (if mixed):

## Stack
- Backend: (Java version, Spring Boot version, build tool Maven|Gradle)
- Frontend: (React|Angular version, state management, build tool)
- Database / messaging / external systems:
- Runtime and deployment:

## Architecture
- Style (e.g. modular monolith, layered, microservices):
- Key boundaries and dependency direction:
- Relevant ADRs:

## Quality Commands (exact commands the agent should run)
- Build:
- Unit tests:
- Integration tests:
- Lint / format:
- Type check:
- Architecture tests:

## Conventions
- Package / folder structure:
- Naming, error handling, logging conventions:
- API style and versioning:

## Do-Not-Touch Areas
- (path or module, reason)

## Deviation Register (legacy / migration)
| Area | Deviation from standard | Severity | Direction |
|---|---|---|---|

## Accepted Risks
| Date | Risk | Decision by | Condition / revisit trigger |
|---|---|---|---|

## Migration Plan (if mode is migration)
- Target state:
- Intermediate states:
- Strategy:
- Current step:
- Rollback approach:
