# Confidence-Based Routing Decision

When to auto-apply AI output vs. send to human review.

```
                    ┌─────────────────────────┐
                    │   AI output received    │
                    │   (with confidence       │
                    │    scores)               │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │  Document/field level   │
                    │  confidence >= threshold?│
                    └────────────┬────────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │ No               │                  │ Yes
              ▼                  │                  ▼
    ┌─────────────────┐          │       ┌─────────────────┐
    │ Route to        │          │       │ Business rules   │
    │ human review    │          │       │ passed?         │
    │ queue           │          │       └────────┬────────┘
    └─────────────────┘          │                │
                                │     ┌──────────┼──────────┐
                                │     │ No       │          │ Yes
                                │     ▼          │          ▼
                                │  ┌─────────┐   │   ┌─────────────┐
                                │  │ Review  │   │   │ Auto-apply  │
                                │  │ queue   │   │   │ (optional:  │
                                │  └─────────┘   │   │  audit log) │
                                │                │   └─────────────┘
                                │                │
                                └────────────────┘
```

## Thresholds

- **Configurable**: By document type, tenant, or risk level.
- **Critical fields**: Some fields (e.g., amount, date, party) may require human check regardless of score; treat as “confidence = 0” for routing if you want them always reviewed.
- **Document vs. field**: If any critical field is low, route whole document to review; or allow partial auto-approve for non-critical fields only (more complex).

## Product Choices

- **Strict**: High threshold (e.g., 0.95) → more review volume, fewer errors.
- **Relaxed**: Lower threshold (e.g., 0.85) → less review volume, higher error risk.
- **Adaptive**: Start strict; relax over time as you measure error rates and user overrides.

See **ai-document-ingestion-workflow** (`architecture/confidence-routing.md`) for more detail.
