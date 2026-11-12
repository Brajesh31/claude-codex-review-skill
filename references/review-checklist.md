# Code Review Checklist

Review the changed code and its relevant context. Do not treat every checklist item as a presumed defect.

## Correctness
- [ ] Inputs, boundaries, nullability, and invalid states are handled.
- [ ] Control flow and state transitions match intended behavior.
- [ ] Error paths preserve useful diagnostics and safe recovery.
- [ ] Async work, cancellation, and retries are correct.

## Security and data
- [ ] Authentication and authorization are enforced at the correct boundary.
- [ ] Untrusted input is validated or safely encoded.
- [ ] Secrets and sensitive data are not exposed.
- [ ] Data writes, migrations, and transactions preserve integrity.

## Reliability and compatibility
- [ ] Concurrency and resource cleanup are safe.
- [ ] Public interfaces and supported versions remain compatible.
- [ ] External calls have appropriate timeout and failure handling.
- [ ] Tests cover meaningful changed behavior.

## Evidence threshold
For every finding, record the exact location, a reproducible failure scenario, concrete impact, and a practical fix. Remove speculative or style-only findings.
