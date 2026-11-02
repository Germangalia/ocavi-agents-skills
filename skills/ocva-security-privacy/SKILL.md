---
name: ocva-security-privacy
description: Validation, authorization, privacy, secure-connectivity assumptions, and external-transfer constraints in OCAVS, OCAVM, and OCAVI. Load for security-sensitive protocol work.
---

# OCVA Security and Privacy

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when implementing message validation, permission checks, identity-sensitive processing, privacy controls, transfer descriptors, security event handling, or security conformance cases.

## Key References

- [OCAVS connectivity](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/02-security/02-01-security-and-connectivity.md), [message validation](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/02-security/02-02-message-validation.md), [authorization, privacy, transfers](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/02-security/02-03-authorization-privacy-transfers.md)
- [OCAVM connectivity](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/02-security/02-01-security-and-connectivity.md), [message validation](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/02-security/02-02-message-validation.md), [privacy and data protection](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/02-security/02-03-privacy-and-data-protection.md)
- [OCAVI connectivity](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/02-security/02-01-security-and-connectivity.md), [message validation](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/02-security/02-02-message-validation.md), [authorization, privacy, transfers](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/02-security/02-03-authorization-privacy-transfers.md)

## Validation and Authorization

- Follow the selected specification's ordered checks: header and message validity, payload/schema constraints, domain/state rules, and operation authorization, in the defined order.
- Reject invalid requests before applying business state changes. Preserve the specified rejection atomicity and status result.
- Enforce the operation's permission and role rules using the trusted identity context available to the implementation. Do not accept self-asserted payload fields as proof of identity.
- Keep connection/session security controls separate from application-level role, resource, and operation authorization.
- Record and correlate security-relevant outcomes only as the relevant protocol permits.

## Privacy and Transfer Rules

- Apply data minimization and only transmit fields required by the operation.
- OCAVI uses pseudonymous references and tokenized payment data; raw card details, PAN, CVV, biometrics, and direct personal identity data must not be introduced into protocol messages.
- OCAVS restricts identity and sensitive data and defines constrained finite external transfers. Validate destination, expiry, size/content limits, authorization scope, and integrity requirements before transfer acceptance.
- Do not place credentials, bearer secrets, or reusable authorization material in transfer descriptors, logs, or error details.
- For OCAVM, use its peer identity, message integrity, freshness, and privacy rules; do not import OCAVI or OCAVS permission names.

## Common Pitfalls

- Validating application permissions after state mutation.
- Treating authenticated connectivity as permission to access every resource.
- Logging secrets, personal data, or full sensitive payloads.
- Using direct identity or raw payment data where pseudonymous/tokenized data is required.
- Accepting an external URL without the specification's destination and content checks.
- Copying a permission string or authorization rule across protocols.
