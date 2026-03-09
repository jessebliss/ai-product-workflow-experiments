# Product Principles for AI-Assisted Workflows

## 1. Augment, Don’t Replace

AI suggests, drafts, and recommends. Humans decide, approve, and sign off. Position AI as a productivity layer, not a replacement for judgment.

## 2. Clear Boundaries

- Document which steps are AI-generated vs. human-confirmed.
- In UI, label “AI suggestion” or “Draft” so users know what they’re approving.
- Avoid “invisible” AI that acts without clear indication.

## 3. Audit and Explainability

- Log: input to AI, output, confidence, and human action (accept / edit / reject).
- Support “why did we get this suggestion?” (e.g., similar cases, source document).
- Retain enough context for compliance and dispute resolution.

## 4. Graceful Degradation

- If AI is down or slow, workflow continues: human does the step manually.
- If confidence is low, route to human instead of guessing.
- Design so that “no AI” is a valid, supported path.

## 5. Feedback Loops

- Capture overrides and rejections to improve prompts, thresholds, and models.
- Use feedback with appropriate consent and data governance.
- Measure acceptance rate, edit rate, and time-to-complete to assess value.

## 6. Safeguards by Default

- Prefer routing to human when in doubt.
- Critical actions (payments, legal, irreversible) always require explicit human approval.
- Rate limits and circuit breakers to limit blast radius of model issues.

## 7. User Control

- Users can turn off or reduce AI assistance where supported.
- Override and “reject AI” must be easy and never penalized.
- Explain how to correct the system (e.g., feedback form, support path).
