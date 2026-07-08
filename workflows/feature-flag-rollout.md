# Feature Flag Rollout for AI Workflows

Use feature flags to ship AI-assisted behavior safely without forcing a single global cutover.

## Flag dimensions

| Flag type | Example | Use case |
|-----------|---------|----------|
| `cohort` | `ai_draft_enabled_for_team_ids` | Pilot with one operations team |
| `percentage` | `ai_triage_rollout_percent` | Gradual traffic ramp |
| `document_type` | `ai_invoice_extraction_enabled` | Scope by content risk |
| `kill_switch` | `ai_features_disabled` | Immediate rollback lever |

## Rollout sequence

1. **Internal only** (employees) for one week.
2. **Pilot cohort** (5-10% of eligible traffic) with daily guardrail review.
3. **Expanded cohort** (25-50%) if override and incident metrics remain stable.
4. **General availability** with kill switch retained for 30 days.

## Required telemetry per flag evaluation

- `flag_key`, `variant`, `subject_id`
- AI model/prompt version
- Human action (`accepted`, `edited`, `rejected`)
- Latency and estimated cost

## Rollback triggers

Disable the flag immediately when:

- Guardrail metric breaches threshold for two consecutive windows
- P1 incident is opened for model quality or data leakage
- Cost per successful workflow exceeds budget by more than 25%

See `notes/rollout-guardrails-checklist.md` for the full checklist.
