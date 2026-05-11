# Evaluation Dataset Guide

How to build and maintain evaluation sets for AI-assisted operational workflows so quality is measurable and regressions are caught before customers see them.

## Principles

- **Representative**: Cover frequent cases, high-risk cases, and known edge cases in proportion to business impact (not uniform random).
- **Stable labels**: “Gold” labels and expected outputs should be versioned and owned (team + refresh cadence).
- **Stratified**: Slice by segment (document type, language, product line, customer tier) to avoid hidden drops in one slice.

## Dataset tiers

| Tier | Purpose | Size |
|------|---------|------|
| **Smoke** | CI / deploy gate; fast | Tens of examples |
| **Regression** | Catch known bugs after prompt or model change | Hundreds |
| **Benchmark** | Quarterly quality reporting | Thousands (if feasible) |

## Label types

- **Extraction**: Field-level expected values + acceptable variants (e.g., date formats).
- **Classification**: Expected label set + ambiguity rules (“unknown” is valid).
- **Summarization / recommendations**: Rubric-based human scores (1–5) plus optional reference text.

## Hard negatives

Include cases where the model should **not** act or should route to human:

- Low-quality scans, conflicting fields, out-of-domain documents.
- Prompt-injection patterns in user-provided text (for chat/email workflows).

## Governance

- Document consent and retention for examples containing PII.
- Prefer synthetic or redacted data for broadly shared sets.

## Release gate example

- Smoke pass rate ≥ 98% and no critical-field regressions vs. previous release.
- Any regression in **high-risk slice** blocks ship until fixed or explicitly waived with sign-off.
