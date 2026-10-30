---
name: ocva-conformance
description: Conformance classes, status catalogs, state-machine requirements, examples, limits, and evidence for OCAVS, OCAVM, and OCAVI. Load when planning verification or assessing compliance.
---

# OCVA Conformance

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when writing conformance tests, reviewing an implementation claim, mapping requirements to evidence, or preparing a release verification plan.

## Key References

- [OCAVS conformance](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/06-compliance/06-01-conformance.md), [status codes](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/06-compliance/06-02-status-codes.md), [state-machine conformance](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/06-compliance/06-03-state-machine-conformance.md), and `appendix/`
- [OCAVM conformance](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/06-compliance/06-01-conformance.md), [status codes](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/06-compliance/06-02-status-codes.md), [state-machine conformance](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/06-compliance/06-03-state-machine-conformance.md), and `appendix/`
- [OCAVI conformance](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/06-compliance/06-01-conformance.md), [status codes](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/06-compliance/06-02-status-codes.md), [state-machine conformance](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/06-compliance/06-03-state-machine-conformance.md), and `appendix/`

## Conformance Workflow

1. Pin the repository and specification version under review.
2. Identify the conformance class/profile, endpoint role, and applicable mandatory operations.
3. Trace each requirement to its normative owner and defined evidence.
4. Build positive tests for valid requests, responses, and permitted transitions.
5. Build negative tests for malformed fields, unauthorized operations, invalid state, stale data, duplicate operations, ordering/deadline failures, and profile incompatibility as applicable.
6. Verify exact status codes, retry categories, required response fields, and state outcomes.
7. Exercise restart/reconnect and recovery behavior when the specification defines it.
8. Keep test evidence reproducible and distinguish test coverage from a formal interoperability claim.

## Rules

- The conformance section and operation definitions control what is required; examples help illustrate but do not replace normative requirements.
- Test every allowed and prohibited transition in the applicable state-machine conformance document.
- Derive expected status and retry behavior from that protocol's status catalog.
- Validate complete payload contracts, including cardinality, enum values, limits, conditional fields, idempotency, and revision behavior.
- Keep each protocol's test vectors and requirement mappings separate.
- Do not infer a certification level or interoperability result from the presence of a passing unit test suite alone.

## Common Pitfalls

- Testing only successful request/response paths.
- Treating a checklist's completion marker as independent implementation evidence.
- Checking enum membership while missing cross-field or lifecycle constraints.
- Assuming status code values or retry meanings are shared across protocols.
- Claiming interoperability without the independent implementation/evidence required by the repository's release posture.
