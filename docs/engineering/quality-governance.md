# Quality Governance

## 1. Objective

Quality is fitness for the intended use under stated constraints. It is not a fixed checklist
whose every item must be applied to every project.

## 2. Quality Dimensions

Evaluate relevant dimensions:
- Functional correctness and acceptance criteria.
- Architecture and dependency boundaries.
- Readability, maintainability, and changeability.
- Testability and verification.
- Security, privacy, and data integrity.
- Performance and resource efficiency.
- Reliability and failure handling.
- Observability and operability.
- Accessibility and user experience.
- Documentation and supportability.

## 3. Applicability Status

For each material dimension, use one of:
- Required: mandated by security, contract, policy, or explicit requirement.
- Applicable: relevant and proportionate to the change.
- Not applicable: no meaningful bearing on this scope; explain briefly when non-obvious.
- Deferred: intentionally postponed; record rationale, owner or trigger where possible, and risk.
- Not verified: not checked or evidence unavailable.

Never convert "not verified" into "passed". Do not use "not applicable" to hide missing work.

## 4. Risk-Based Testing

Choose test levels based on behavior, boundaries, failure modes, and change risk:
- Unit tests for isolated domain logic and decision-heavy behavior.
- Integration tests for persistence, framework wiring, messaging, and external boundaries.
- Contract tests for independently evolving consumers and providers.
- Component/UI tests for meaningful user interaction and rendering behavior.
- End-to-end tests for critical user journeys and system-level integration.
- Non-functional tests for performance, resilience, security, accessibility, and capacity when
  requirements or risk justify them.

Do not chase coverage percentages without considering assertion quality and risk. Avoid brittle
tests coupled to implementation details.

## 5. Test Design Expectations

Consider:
- Happy paths and meaningful edge cases.
- Invalid input and authorization failures.
- Boundary values and state transitions.
- Timeouts, retries, duplicate requests, and partial failures where relevant.
- Data integrity and transaction behavior.
- Determinism, isolation, and test data lifecycle.

Use test doubles deliberately. Prefer realistic integration tests at important boundaries when
mocks would conceal framework or infrastructure behavior.

## 6. Security and Privacy Quality Gate

At relevant trust boundaries assess:
- Authentication and authorization.
- Input validation and output encoding.
- Injection and unsafe deserialization.
- Secret and sensitive-data handling.
- Dependency and supply-chain risk.
- Data exposure through logs, errors, and APIs.
- Abuse cases, rate limits, and resource exhaustion.
- Secure configuration and least privilege.

The applicable threat model depends on the system. Do not claim a security review is complete
based solely on a checklist.

## 7. Performance and Reliability

Use requirements and evidence to determine whether performance or reliability testing is
needed. Consider workload, concurrency, latency, throughput, resource use, caching, database
access, timeouts, retries, idempotency, and recovery. Do not add complexity without a measured
or credible need.

## 8. Deterministic Verification

Prefer automated enforcement for objective requirements:
- Formatter and linter.
- Compiler and type checker.
- Unit and integration test suites.
- Architecture tests.
- API/schema compatibility checks.
- Dependency and security scanning.
- Build and packaging checks.
- CI quality gates.

The agent must inspect project scripts and use the repository's actual commands. Do not invent
commands or assume a tool is installed.

## 9. Completion Evidence

Report:
- Exact commands or checks executed (where practical).
- Pass/fail outcome and relevant summary.
- Checks not run and why.
- Known flaky, environment-dependent, or inconclusive results.
- Remaining risks and deferred work.

A successful build is not proof of functional correctness. Passing tests are not proof of
security. State the scope of evidence accurately.
