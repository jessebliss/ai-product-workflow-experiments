# Incident Response for AI Features

Runbook-style guidance when AI-assisted workflows degrade (quality drops, cost spikes, provider outage, or suspected harmful outputs).

## Severity levels (example)

| Level | Example | Response |
|-------|---------|----------|
| **SEV1** | Wrong financial/legal data auto-applied | Disable auto-apply; force human review; executive comms if customer impact |
| **SEV2** | Elevated error rate or latency | Enable circuit breaker; scale review capacity; status page if external |
| **SEV3** | Minor quality drift | Monitor; schedule prompt/schema rollback or fix |

## Immediate actions

1. **Triage**: Confirm scope (model version, prompt id, integration, region, cohort).
2. **Mitigate**: Feature flag off auto-paths; raise routing to human review; reduce traffic to new variant.
3. **Communicate**: Internal incident channel + customer messaging per policy.
4. **Preserve evidence**: Export sample failing inputs/outputs with correlation IDs (no unnecessary PII retention).

## Technical levers

- **Rollback**: Revert model, prompt, or schema version; redeploy last known good.
- **Kill switch**: Global or per-tenant disable for AI suggestions only (manual path still works).
- **Throttle**: Lower max tokens, concurrency, or document size temporarily.

## Post-incident

- Root cause: model regression, data drift, mapping bug, rate limit storm, etc.
- Action items: add regression cases (`notes/evaluation-dataset-guide.md`), tighten guardrails, improve dashboards.
- Blameless review: focus on systems and gates, not individuals.

## Cross-repo links

- Ingestion reliability: **ai-document-ingestion-workflow** `architecture/failure-modes-and-recovery.md`
- Integration retries and DLQ: **saas-integration-patterns** `patterns/error-taxonomy.md`, `examples/dead-letter-event.json`
