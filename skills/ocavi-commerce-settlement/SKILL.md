---
name: ocavi-commerce-settlement
description: OCAVI quotes, tariffs, invoices, tokenized payments, settlement, reconciliation, and disputes. Load for financial workflow code, contract reviews, or related conformance cases.
---

# OCAVI Commerce and Settlement

## Specification Versions

This skill references **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when implementing quote/tariff logic, invoice creation, payment tokenization/authorization/capture, settlement, reconciliation, dispute creation/resolution, or associated status/state handling.

## Key References

- Types: [pricing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-05-pricing.md), [billing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-07-billing.md), [payments](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-08-payments.md), [disputes and reconciliation](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-09-disputes.md)
- Operations: [quotes/tariffs](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-03-quotes-tariffs.md), [billing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-08-billing.md), [payments](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-09-payments.md), [settlement](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-10-settlement.md), [reconciliation](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-11-reconciliation.md), [disputes](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-12-disputes.md)
- [Cross-domain application behavior](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/05-application/05-01-application-behavior.md), [payment and settlement workflow](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/appendix/C-operation-workflows.md)

## Rules

- Keep quote, tariff, invoice, payment authorization, payment capture, settlement, reconciliation, and dispute states distinct.
- Use explicit currency codes and integer minor-unit amounts. Do not use floating-point money.
- Use tokenized payment data only. Never add raw card data, PAN, CVV, or biometric data to a message.
- Follow operation-specific roles, idempotency identities, revisions, deadlines, status mappings, and state transitions.
- A successful authorization is not proof of capture, settlement, or reconciliation.
- Preserve financial references and evidence links as pseudonymous identifiers and constrained references.
- Handle duplicate requests according to the operation's idempotency rules; do not create duplicate invoices, captures, or settlements on retry.
- Follow dispute eligibility, evidence, resolution, and terminal state requirements.

## Common Pitfalls

- Treating authorization, capture, settlement, and reconciliation as one event.
- Retrying a financial mutation without its idempotency key.
- Rounding or changing currency units during serialization.
- Inferring invoice/payment state from a booking state.
- Including personal identity or raw payment data in logs, errors, or payloads.
- Resolving a dispute without the defined resolution result and status transition.
