# Use Case: AI-Assisted Document Analysis

## Summary

Documents (invoices, contracts, forms) are ingested; AI extracts structured data and optionally summarizes. Humans validate critical fields and approve record creation.

## Flow

1. Document uploaded and stored.
2. OCR + LLM extraction produces structured draft (entities + confidence).
3. Business rules run; failures and low-confidence items flagged.
4. Human sees draft in review UI; can edit, approve, or reject.
5. On approve: record created in CRM/case system; document linked; audit log written.

## Product Considerations

- **High-risk fields**: Amounts, dates, party names often require human confirmation even when confidence is high. Make this configurable by document type.
- **UI**: Show confidence per field (e.g., color or icon); make edits easy; show “source” region in document when possible.
- **Batching**: Allow “approve all” for high-confidence, rule-passing documents with a single action; support bulk reject with reason.
- **Feedback loop**: Store corrections as potential training signal; ensure privacy and consent before using for model updates.

## Where AI Stops

- AI does not create the final record without approval (or without passing a strict auto-approve policy).
- AI does not decide document type when ambiguous; human selects or confirms.
- Rejections and overrides are always human-driven.

## Reference

See **ai-document-ingestion-workflow** for pipeline architecture, confidence routing, and example schemas.
