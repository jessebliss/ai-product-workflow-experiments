# Use Case: Conversation Transcript Analysis

## Summary

Call or chat transcripts are analyzed by AI to produce summaries, action items, and topic tags. Humans verify and assign owners; outcomes sync to task or case systems.

## Flow

1. Transcript ingested (post-call or real-time stream).
2. AI generates: short summary, bullet action items, suggested topics/tags, optional sentiment or escalation signal.
3. Human reviews summary and items; can edit, add, or remove; assigns owners and due dates.
4. Approved actions create tasks or case updates; summary attached to case/contact record.

## Product Considerations

- **Real-time vs. post-call**: Post-call is simpler and allows full-context summary; real-time can support live coaching or alerts but is harder and noisier.
- **Speakers**: If transcript has speaker labels, preserve them; summary can say “Customer reported X; agent suggested Y.”
- **Verification**: Link summary bullets to transcript segments (timestamps or quotes) so humans can verify without re-reading the whole transcript.
- **Privacy**: Transcripts may contain PII; access control and retention policies must be clear; consider redaction or summarization-only in some regions.

## Where AI Stops

- AI does not assign owners or due dates unless explicitly configured as a suggestion; human confirms.
- AI does not close cases or mark items done; human (or downstream automation with human-defined rules) does.
- Escalation or “at-risk” signals are recommendations; human decides whether to escalate.

## Integration

Fits well with **saas-integration-patterns**: webhooks for new transcripts; API to create tasks or update CRM; idempotency by transcript_id and item_id.
