# Prompt Change Review Template

Use this template before promoting prompt or model changes to production AI workflows.

## Change summary

- **Workflow**:
- **Owner**:
- **Prompt version (from → to)**:
- **Model (from → to)**:
- **Change type**: `bugfix` | `quality` | `cost` | `latency`

## Expected impact

- **Primary metric expected delta**:
- **Guardrail metrics at risk**:
- **Affected user cohorts**:

## Validation evidence

- [ ] Offline eval run on versioned dataset (`evaluation-dataset-guide.md`)
- [ ] Regression cases reviewed for high-risk fields
- [ ] Side-by-side examples attached (before/after)
- [ ] Rollback plan documented (previous prompt/model artifact pinned)

## Release decision

- **Decision**: `approve` | `approve_with_monitoring` | `reject`
- **Approver**:
- **Monitoring window**:
- **Rollback owner**:

## Post-release follow-up (72 hours)

- Override rate delta:
- Incident count:
- Cost delta:
- Follow-up action:
