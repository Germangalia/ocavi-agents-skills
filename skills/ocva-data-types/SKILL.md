---
name: ocva-data-types
description: Canonical scalar, object, enum, time, unit, identity, and geospatial representations in the three OCVA specifications. Load when creating, validating, or mapping payload fields.
---

# OCVA Data Types

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load this skill when defining schemas, serializing messages, validating field values, translating data between systems, or reviewing examples.

## Key References

- [OCAVS general types](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/03-data-types/03-01-general.md) and all files in its `03-data-types/` directory
- [OCAVM general types](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/03-data-types/03-01-general.md) and all files in its `03-data-types/` directory
- [OCAVI general types](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-01-general.md) and all files in its `03-data-types/` directory
- The selected operation's request/response field tables and the selected repository's `appendix/B-message-examples.md`.

## Rules

- Use the canonical type owner for each field. Do not redefine a shared or domain type inside an operation schema.
- Preserve exact field names, type names, cardinality, null/absence semantics, enum spelling, and closed-enum behavior from the selected version.
- Keep UUIDv7 identifiers distinct by purpose: message identity, resource identity, correlation, sequence, and business idempotency identities are not interchangeable.
- Use UTC ISO 8601 timestamps and exact precision/format requirements from the relevant protocol.
- Keep physical units and coordinate systems explicit. Do not convert units without a documented mapping and range check.
- OCAVI monetary values use integer minor units with explicit currency codes; do not use floating-point currency amounts.
- Validate nested-object constraints, exclusive-member rules, bounds, and semantic relationships, not only JSON syntax.
- Treat a missing optional field according to its documented presence rule; do not silently turn absence into `null`, an empty string, or a default.

## Domain Type Areas

| Protocol | Types to consult |
| --- | --- |
| OCAVS | Vehicle/capability and mission types; supervision, telemetry, perception/acquisition; energy, diagnostics, monitoring, firmware, ODD, geofence, and event types |
| OCAVM | General, awareness, danger, maneuver, intersection, merge, platoon, infrastructure, and time-window types |
| OCAVI | Participant, service, booking, pricing, session, billing, payment, settlement, dispute, and reconciliation types |

## Common Pitfalls

- Reusing a similarly named enum from a different protocol.
- Treating an identifier or timestamp as an unconstrained string.
- Confusing protocol status, operation result, and resource lifecycle enums.
- Serializing amounts as decimal floating-point values.
- Dropping units, precision, cardinality, or conditional-presence constraints during schema generation.
