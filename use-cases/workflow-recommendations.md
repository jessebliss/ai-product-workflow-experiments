# Use Case: Workflow Recommendations

## Summary

While a user works in a case or ticket, AI suggests the next step or a response template based on similar past cases. The user accepts, edits, or ignores; the system logs the outcome for learning.

## Flow

1. User is viewing a case (type, history, content).
2. System calls recommendation service: “What next step or template fits?”
3. AI returns one or more suggestions with optional explanation (“Similar to case #X”, “Common resolution for this category”).
4. User accepts (maybe with edits), uses a different action, or dismisses.
5. Acceptance/rejection and edits are logged; can be used to tune recommendations and measure usefulness.

## Product Considerations

- **Explainability**: Users trust suggestions more when they see why (“3 similar cases closed with this template”). Surfaces can be simple (e.g., “Based on similar cases”) or detailed (links to those cases if permitted).
- **Cold start**: When few similar cases exist, show a generic set or “No strong recommendation”; avoid low-quality suggestions.
- **Loops**: Avoid reinforcing one dominant action (e.g., “always suggest template A”). Use diversity or decay so other options get exposure; monitor for feedback loops.
- **Scope**: Define clearly what “next step” means: next status, next template, next assignee, or full playbook. Start narrow and expand.

## Where AI Stops

- AI suggests; it does not execute. User must confirm before any state change (status, assignment, sending a message).
- AI does not have access to perform actions on its own; it only returns suggestions to the UI or workflow engine.
- Final accountability for the chosen action stays with the human (and, where relevant, the organization’s policies).

## Metrics

- Suggestion acceptance rate; edit rate; time-to-resolution for accepted vs. rejected suggestions.
- Track by case type and user segment to improve relevance and avoid bias.
