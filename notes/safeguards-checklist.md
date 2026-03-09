# Operational Safeguards Checklist

Use when designing or reviewing an AI-assisted workflow.

## Before Launch

- [ ] **Confidence thresholds** defined and configurable (no hardcoded magic numbers).
- [ ] **Critical fields** identified; always require human confirmation for those fields (or document exception).
- [ ] **Human review queue** exists for low-confidence and rule-failure cases; SLA and ownership clear.
- [ ] **Audit trail** captures: input, AI output, confidence, human action, user, timestamp.
- [ ] **Override and reject** paths implemented and easy to use; reason optional but encouraged.
- [ ] **Idempotency** for any create/update triggered by AI or approval (see **saas-integration-patterns**).
- [ ] **Rate limits / circuit breaker** for AI calls to avoid cascade failures or cost spikes.
- [ ] **Graceful degradation** tested: workflow completes when AI is unavailable or timed out.

## Compliance and Risk

- [ ] **Regulated decisions**: Human-in-the-loop required where regulation mandates it; documented.
- [ ] **PII and retention**: Access control and retention policy for documents and transcripts; redaction if needed.
- [ ] **Bias and fairness**: Consider sampling and QA for high-impact outcomes; monitor by segment if applicable.
- [ ] **Terms and consent**: Users and/or customers informed about AI use and data handling where required.

## Ongoing

- [ ] **Monitoring**: Error rate, latency, review queue depth, acceptance/edit/reject rates.
- [ ] **Alerts**: Spike in rejections, queue backlog, AI provider errors.
- [ ] **Feedback loop**: Overrides and corrections logged and (where appropriate) used for model or rule tuning.
- [ ] **Documentation**: Runbooks for “AI down” and “suspected bad model behavior”; escalation path.

## Product

- [ ] **Explainability**: Users can understand why a suggestion was made (e.g., “similar to case X”).
- [ ] **Control**: Users can reduce or disable AI assistance where the product supports it.
- [ ] **Metrics**: Define success (e.g., time saved, error rate, user satisfaction) and track over time.
