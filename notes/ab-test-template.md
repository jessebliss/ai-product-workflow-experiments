# A/B Test Template (AI Workflow Feature)

## Experiment Name

- `exp_name`:
- `owner`:
- `start_date`:
- `end_date`:

## Hypothesis

- If we enable `<feature>`, then `<user segment>` will see `<expected outcome>`.

## Variants

- **Control (A)**: Current workflow.
- **Treatment (B)**: Workflow with AI assistance.

## Eligibility / Segmentation

- Included users/cases:
- Excluded users/cases:
- Randomization unit (user, account, case, etc.):

## Metrics

- **Primary metric**:
- **Guardrail metric 1**:
- **Guardrail metric 2**:
- **Operational metric** (latency/cost/queue):

## Success Criteria

- Minimum lift required:
- Maximum acceptable guardrail regression:

## Rollout Plan

- Stage 1:
- Stage 2:
- Stage 3:
- Rollback trigger:

## Results

- Sample sizes (A/B):
- Primary metric delta:
- Guardrail results:
- Decision (ship / iterate / rollback):
- Follow-up actions:
