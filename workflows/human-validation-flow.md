# Human Validation Flow

Generic flow for any AI-assisted step that requires human validation before a system action.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                     HUMAN VALIDATION FLOW                                │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│   AI / System                Validation Gate                 Downstream │
│                                                                         │
│   ┌──────────────┐           ┌──────────────────┐           ┌─────────┐ │
│   │ AI produces  │           │  Human reviews   │           │ Execute │ │
│   │ output       │ ────────▶ │  • Accept        │ ────────▶ │ action  │ │
│   │ (draft,      │           │  • Edit + accept  │  approve  │ (e.g.   │ │
│   │  suggestion) │           │  • Reject        │           │  create │ │
│   └──────────────┘           └──────────────────┘           │  record)│ │
│          │                            │                     └─────────┘ │
│          │                            │  reject                           │
│          │                            ▼                                  │
│          │                     ┌──────────────────┐                      │
│          │                     │  Log reason;     │                      │
│          │                     │  optional        │                      │
│          │                     │  escalation      │                      │
│          │                     └──────────────────┘                      │
│          │                                                               │
│          ▼                                                               │
│   ┌──────────────┐                                                      │
│   │ Audit:       │  (input, output, confidence, human action, user, ts)  │
│   │ store for    │                                                      │
│   │ compliance   │                                                      │
│   └──────────────┘                                                      │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

## Decision Points

| Condition | Route |
|-----------|--------|
| High confidence + optional approval policy | Can offer “auto-accept” with audit; or still require one-click accept. |
| Low confidence or rule failure | Must go to human; no auto-accept. |
| Human edits | Stored as “approved version”; original AI output retained for audit and analytics. |
| Human rejects | No downstream action; reason captured; can trigger escalation or exception workflow. |

## Implementation Notes

- **Queue**: Items needing validation sit in a queue (per user, per team, or global). SLA and prioritization are product decisions.
- **Notifications**: Optional email/in-app notification when item is assigned or when it’s been waiting too long.
- **Bulk actions**: Where safe, allow “approve all” for a filtered set (e.g., all high-confidence, rule-passing items in a batch).
