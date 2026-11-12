---
name: codex-review
description: Perform a professional code review with Codex assistance, prioritize actionable defects, and generate a CHANGELOG entry from verified changes when requested or appropriate.
---

# Codex Review

Conduct a structured, evidence-based code review with Codex as the analysis engine when available. Focus on correctness, security, reliability, maintainability, and regressions. A polished review is not a list of stylistic preferences.

## Review objectives

Find defects that matter to users or operators:
- incorrect behavior and edge cases;
- regressions introduced by the change;
- authorization, authentication, privacy, or input-validation weaknesses;
- data loss, race conditions, resource leaks, and failure-handling gaps;
- broken compatibility or public contracts;
- missing tests for meaningful behavior.

Do not report speculative concerns as confirmed bugs.

## Workflow

### 1. Establish review scope
- Inspect the repository, current branch, base branch, and working tree.
- Identify the exact diff or commit range being reviewed.
- Read the relevant project instructions and adjacent implementation.
- Separate pre-existing issues from issues introduced by the change.

### 2. Analyze with Codex
When Codex CLI is available and the user requested or enabled it:
- provide the exact diff and review objective;
- ask for findings grounded in concrete code paths;
- request file and line references;
- ask the model to distinguish confirmed defects from questions and suggestions.
If Codex is unavailable, state that and use another review method only when the user permits it.

### 3. Validate findings
For every candidate finding:
- inspect the referenced code;
- trace relevant callers, data flow, and error handling;
- check whether tests or invariants already cover the behavior;
- reproduce the issue when practical;
- remove findings based only on assumptions or personal style.

### 4. Rank findings
Use these practical severities:
- **Critical:** likely broad compromise, severe data loss, or major outage.
- **High:** serious security or correctness defect with material impact.
- **Medium:** meaningful functional defect or reliability risk in a realistic scenario.
- **Low:** limited-impact defect or maintainability issue with a concrete consequence.
- **Informational:** non-blocking suggestion, clearly separated from defects.

A finding should include the affected location, scenario, impact, and a direct recommendation.

### 5. Generate a CHANGELOG entry
When a changelog is requested, or the repository uses one and the user expects it:
- inspect the existing changelog format and current release section;
- derive entries only from verified changes;
- group changes by Added, Changed, Fixed, or Security where the project uses those headings;
- avoid duplicating existing entries;
- do not invent issue numbers, release versions, or user-visible impact.

Do not create a new changelog format if the repository already has one.

### 6. Report
Present actionable findings first. If there are no confirmed findings, say so and describe the scope and checks performed. Clearly distinguish an empty finding list from proof that the code is defect-free.

## Finding format

```text
[Severity] Short, specific title
Location: path/to/file.ext:line
Scenario: the conditions that trigger the issue
Impact: the concrete consequence
Recommendation: the smallest reliable correction
```

## Boundaries

- Do not make code changes during a review unless the user asks for fixes.
- Do not commit, push, or open a pull request unless explicitly requested.
- Never modify a changelog without permission when the requested scope is review-only.
- Never fabricate test results, line numbers, issue references, or Codex output.