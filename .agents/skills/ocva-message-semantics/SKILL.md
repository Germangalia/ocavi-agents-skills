---
name: ocva-message-semantics
description: Request and response processing, idempotency, revisions, ordering, deadlines, and application lifecycles across the OCVA protocols. Load when implementing message contracts or stateful workflows.
---

# OCVA Message Semantics

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load this skill when defining message handlers, retries, duplicate handling, resource updates, deadlines, notifications, reconnection recovery, or lifecycle transitions.

## Key References

- [OCAVS message semantics](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/01-architecture/01-02-message-semantics.md), [application behavior](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-01-application-behavior.md), [compatibility](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/05-application/05-02-compatibility.md)
- [OCAVM message semantics](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/01-architecture/01-02-message-semantics.md), [application behavior](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/05-application/05-01-application-behavior.md), [compatibility](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/05-application/05-04-compatibility.md)
- [OCAVI message semantics](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/01-architecture/01-02-message-semantics.md), [application behavior](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/05-application/05-01-application-behavior.md), [compatibility](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/05-application/05-02-compatibility.md)
- The selected protocol's lifecycle documents under `05-application/` and its operation-specific `04-operations/` documents.

## Scope

All three protocols define typed application messages, but their identifiers, ordering rules, idempotency requirements, and lifecycle semantics are protocol-specific. Always use the selected repository's exact operation definition.

## Processing Checklist

1. Identify the protocol, exact message type, endpoint role, profile, and specification version.
2. Validate the message header and payload in the order specified by the protocol.
3. Check the operation's permission, preconditions, deadline, expected revision, and idempotency requirements.
4. Apply a permitted state transition atomically; do not partially mutate state on a rejected request unless the operation explicitly allows it.
5. Return the exact paired response type, required status, and required result fields.
6. Persist the operation identity/deduplication result as required so a retry has the specified outcome.
7. On reconnect, distinguish delivery recovery from application resource reconciliation.

## Rules

- Do not assume every request is idempotent. Check the operation definition and message-semantics rules.
- Do not treat resource revision, message sequence, correlation identity, and business idempotency identity as interchangeable.
- Preserve exact request/response correlation behavior and registered message identifiers.
- Follow the protocol's duplicate, stale, missing-sequence, out-of-order, and deadline outcomes. Do not invent a generic retry response.
- Use the defined lifecycle diagrams and operation rules to decide which transitions are allowed.
- Apply compatibility and feature-profile requirements before accepting an operation.
- A notification, asynchronous acceptance, or empty query result has the meaning specified for that operation; do not infer completion from receipt alone.

## Common Pitfalls

- Performing a state-changing operation twice after a timeout without checking its idempotency contract.
- Accepting a stale resource revision or command sequence.
- Returning a generic error when the specification defines a specific status and retry class.
- Replaying a domain operation merely because the connection was re-established.
- Treating `status` as the lifecycle state of the resource.
