# Rollout Guardrails Checklist

Use this checklist before expanding an AI-assisted workflow beyond a pilot cohort.

## Pre-rollout

- [ ] Primary success metric and one guardrail metric are defined
- [ ] Eval dataset is versioned and covers edge cases (see `evaluation-dataset-guide.md`)
- [ ] Human override path is available in every AI-assisted step
- [ ] Rollback trigger is explicit (error rate, override rate, latency, cost)

## During rollout

- [ ] Cohort size increases in steps (for example 5% → 25% → 100%)
- [ ] Override reasons are captured for model and prompt tuning
- [ ] Incident runbook owner is assigned (see `incident-response-for-ai-features.md`)
- [ ] Cost per successful workflow is tracked weekly

## Post-rollout (first 30 days)

- [ ] Weekly review of override rate and false-positive complaints
- [ ] Sampled human QA on high-risk outputs
- [ ] Prompt/model version changes are logged with before/after metric deltas
- [ ] Deprecation plan exists for temporary manual fallback paths

## Stop conditions

Pause rollout immediately if any of these occur:

- Guardrail metric breaches threshold for two consecutive measurement windows
- Critical-field error rate increases materially versus control
- Support tickets tied to AI output increase without a known external cause
