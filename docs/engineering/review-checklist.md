# Review Checklist

Use this checklist for code reviews, architecture reviews, and security reviews.
Not every item applies to every change. Mark each item as:

- ✅ Pass — verified and acceptable
- ⚠️ Warning — acceptable with noted risk or follow-up
- ❌ Fail — must be resolved before merge
- N/A — not applicable to this change (explain briefly if non-obvious)

---

## 1. Correctness

- [ ] The change does what the requirement states.
- [ ] Edge cases and boundary values are handled.
- [ ] Error paths are handled explicitly, not silently swallowed.
- [ ] No off-by-one errors, null dereferences, or unhandled states.
- [ ] Concurrent access is safe where relevant (race conditions, shared state).
- [ ] Data types and conversions are correct and explicit.

---

## 2. Architecture and Design

- [ ] The change fits within the existing architectural boundaries.
- [ ] No new cyclic dependencies introduced.
- [ ] Dependency direction is correct (high-level policy does not depend on volatile details).
- [ ] Responsibilities are cohesive — no unrelated concerns mixed in one class or module.
- [ ] Abstractions introduced have a clear reason (substitution, testability, or boundary protection).
- [ ] No speculative abstractions or premature generalization.
- [ ] If a new architectural boundary is introduced, an ADR is created or referenced.

---

## 3. Security

- [ ] All untrusted input is validated at the trust boundary.
- [ ] Authorization is enforced server-side for every operation.
- [ ] No secrets, credentials, or PII in code, logs, or error messages.
- [ ] SQL queries use parameterized statements or ORM — no string concatenation.
- [ ] Deserialization of untrusted data is safe.
- [ ] File paths and URLs from user input are sanitized.
- [ ] Dependencies introduced have no known critical vulnerabilities (check CVE/OWASP).
- [ ] API responses do not expose internal structure, stack traces, or sensitive fields.
- [ ] Rate limiting or abuse protection considered for public-facing endpoints.
- [ ] Cryptographic operations use standard libraries — no custom crypto.

---

## 4. Testing

- [ ] New behavior is covered by at least one automated test.
- [ ] Tests verify observable behavior, not implementation details.
- [ ] Happy path, error path, and at least one meaningful edge case are covered.
- [ ] No tests disabled or skipped without a recorded, approved reason.
- [ ] Test data is isolated — tests do not depend on shared mutable state.
- [ ] Integration tests cover persistence, external calls, or framework wiring where relevant.
- [ ] Tests are deterministic — no random data, time-dependent assertions, or flaky sleeps.

---

## 5. Code Quality

- [ ] Code is readable without requiring comments to explain what it does.
- [ ] Naming is clear, consistent with project conventions, and domain-appropriate.
- [ ] No dead code, commented-out blocks, or TODO items left without a tracking reference.
- [ ] Functions and methods have a single, clear responsibility.
- [ ] No unnecessary duplication — but shared abstractions are justified, not forced.
- [ ] Logging is meaningful: errors logged with context, no sensitive data, no noise.
- [ ] No magic numbers or strings — constants are named and placed appropriately.

---

## 6. Performance and Reliability

- [ ] No N+1 query problems introduced.
- [ ] Database queries use appropriate indexes (verify with EXPLAIN where relevant).
- [ ] External calls have timeouts configured.
- [ ] Retry logic (if present) is bounded and accounts for idempotency.
- [ ] No unbounded collections loaded into memory.
- [ ] Caching introduced only where there is a measured or credible need.
- [ ] Resource handles (connections, streams, files) are closed properly.

---

## 7. API and Contract

- [ ] API changes are backward-compatible, or a breaking change has been approved.
- [ ] New endpoints follow the project's API versioning and naming conventions.
- [ ] Response schemas are consistent with existing patterns.
- [ ] Deprecations are marked and communicated, not silently removed.
- [ ] Event or message schemas are versioned if consumed by external systems.

---

## 8. Observability

- [ ] Errors are logged with enough context to diagnose without a debugger.
- [ ] New significant operations emit appropriate log entries (not excessive).
- [ ] Metrics or traces added where the change introduces a new critical path.
- [ ] Health check or readiness probe updated if a new dependency is introduced.

---

## 9. Documentation

- [ ] Public API changes are reflected in API documentation.
- [ ] `PROJECT_CONTEXT.md` updated if architecture, stack, or conventions changed.
- [ ] ADR created or updated for significant durable decisions.
- [ ] README or setup instructions updated if the change affects how to run the project.
- [ ] Non-obvious design choices have a brief inline explanation (not restating the code).

---

## 10. Deployment and Operations

- [ ] Database migrations are backward-compatible with the running version (expand/contract).
- [ ] Configuration changes are documented and defaults are safe.
- [ ] Feature flags or rollout strategy defined for high-risk changes.
- [ ] Rollback path is clear and tested where the change is irreversible.
- [ ] No hardcoded environment-specific values (URLs, credentials, ports).

---

## Review Summary

| Area | Status | Notes |
|---|---|---|
| Correctness | | |
| Architecture | | |
| Security | | |
| Testing | | |
| Code Quality | | |
| Performance | | |
| API / Contract | | |
| Observability | | |
| Documentation | | |
| Deployment | | |

**Overall decision:** Approve / Request Changes / Reject

**Blocking issues:**

**Non-blocking follow-up:**
