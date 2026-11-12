# Codex Code Review

A structured code review workflow that uses Codex-assisted analysis to identify and verify defects in software changes.

## Review areas

- Correctness, edge cases, and error handling.
- Security and access-control issues.
- Data integrity and unsafe migrations.
- Performance, concurrency, and compatibility.
- Test coverage and release risks.

## Workflow

Establish the exact diff and intended behavior, review surrounding code, investigate likely failure paths, and verify each potential finding before reporting it. Keep changelog generation separate from review findings.

## Output

Provide a concise summary, severity-ranked findings with file locations and concrete failure scenarios, remediation guidance, and verification results.

An empty findings list is acceptable when no actionable issue is confirmed. Avoid speculative concerns and style-only objections.
