---
name: review
description: >-
  Run focused role-based reviews. Use when the user asks for code review,
  architecture review, complexity/simplification review, security review,
  design or accessibility review, docs review, spec alignment review, release
  readiness, or asks to review a branch/diff/plan with a specific lens.
argument-hint: "[--as complexity|architecture|security|design|accessibility|docs|spec|release] [target]"
arguments:
  - request
license: MIT
effort: medium
allowed-tools: Bash Read Glob Grep Task
---

# Review

Pick one role first. Run multiple roles only when the user asks, or when finishing a task with broad blast radius.

Lead with findings. Cite files, lines, commands, specs, or screenshots where possible. Do not rewrite code unless the user asks for fixes after the review.

## Routing

| Role | Use for | Reference |
|---|---|---|
| `complexity` | overengineering, maintainability, simplify sweeps | [references/complexity.md](references/complexity.md) |
| `architecture` | boundaries, module shape, coupling, deep modules, alignment | inline role below |
| `security` | auth, secrets, permissions, injection, data exposure | inline role below |
| `design` | UI/UX critique and visual quality | [references/design.md](references/design.md) |
| `accessibility` | WCAG, keyboard, semantics, focus, contrast | [references/accessibility.md](references/accessibility.md) |
| `docs` | README, guides, API docs, release notes | inline role below |
| `spec` | diff vs PRD/issue/plan acceptance criteria | inline role below |
| `release` | readiness, migration, rollback, deploy risk | inline role below |

## Inline Roles

### Architecture

Check whether the change preserves the repo's dominant patterns, keeps boundaries clear, avoids shallow abstractions, and names concepts in the repo's language. Prefer specific smaller alternatives over broad redesigns.

### Security

Look for exposed secrets, unsafe shell construction, auth/authorization bypass, overbroad permissions, injection, SSRF/path traversal, private data leaks, and unsafe dependency or workflow changes. Distinguish confirmed issues from questions.

### Docs

Check whether docs match current behavior, include setup and verification details, avoid stale file paths when unnecessary, and make failure/recovery paths clear.

### Spec

Find the source spec or plan. Report missing requirements, scope creep, and behavior that appears implemented incorrectly. Quote or cite the spec for each finding.

### Release

Check local verification, migrations, config/env changes, rollback path, compatibility, observability, and user-facing risk. Do not approve release when required verification failed.

## Output

```markdown
Findings
1. [severity] path:line - issue, impact, and smallest correction.

Open Questions
- ...

Checks Run
- `command`: result
```
