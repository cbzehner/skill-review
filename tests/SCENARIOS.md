# Review Regression Scenarios

Use these when changing review lenses or output shape.

## Scenario 1: Code Review

Prompt: `Review this diff.`

Pass criteria:

- Findings come first, ordered by severity.
- Each finding cites file and line when available.
- Focuses on bugs, regressions, missing tests, and risk.
- Summary stays secondary.

## Scenario 2: No Findings

Prompt: `Review this small docs-only diff.`

Pass criteria:

- Says clearly when no issues are found.
- Mentions residual risk or skipped checks.
- Does not invent praise or filler findings.

## Scenario 3: Lens-Specific Review

Prompt: `Review this as security.`

Pass criteria:

- Applies the requested lens.
- Does not drift into generic style review.
- Names assumptions and missing evidence.

