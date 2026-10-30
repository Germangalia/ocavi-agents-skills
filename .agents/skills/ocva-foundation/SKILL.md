---
name: ocva-foundation
description: Scope, terminology, roles, deployment, profiles, and protocol boundaries for OCAVS, OCAVM, and OCAVI. Load before designing or reviewing OCVA protocol behavior.
---

# OCVA Foundation

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load this skill when a task involves selecting a protocol, identifying endpoint roles, interpreting shared terms, choosing a feature profile, or describing a deployment across OCAVS, OCAVM, and OCAVI.

## Key References

- [OCAVS scope](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/00-foundation/00-01-scope-and-overview.md), [terminology](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/00-foundation/00-02-terminology-and-conventions.md), [deployment](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/00-foundation/00-03-deployment.md), [core concepts](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/01-architecture/01-01-core-concepts.md), [profiles](https://github.com/Germangalia/OCAVS/blob/v0.1.0/ocavs-specification/01-architecture/01-03-feature-profiles.md)
- [OCAVM scope](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/00-foundation/00-01-scope-and-overview.md), [terminology](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/00-foundation/00-02-terminology-and-conventions.md), [deployment](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/00-foundation/00-03-deployment.md), [core concepts](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/01-architecture/01-01-core-concepts.md), [profiles](https://github.com/Germangalia/OCAVM/blob/v0.1.0/ocavm-specification/01-architecture/01-03-feature-profiles.md)
- [OCAVI scope](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/00-foundation/00-01-scope-and-overview.md), [terminology](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/00-foundation/00-02-terminology-and-conventions.md), [deployment](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/00-foundation/00-03-deployment.md), [core concepts](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/01-architecture/01-01-core-concepts.md), [profiles](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/01-architecture/01-03-feature-profiles.md)

## Protocol Selection

| Protocol | Use it for | Primary roles |
| --- | --- | --- |
| OCAVS | Vehicle-to-server application and fleet/device management | Connected autonomous vehicle (CAV), central CAV management system (CCMS) |
| OCAVM | Short-range vehicle-to-vehicle and vehicle-to-infrastructure coordination | On-board units and roadside/infrastructure participants as defined by the selected profile |
| OCAVI | Platform-to-platform service interoperability | Mobility service provider (MSP), service operator (SO), infrastructure service provider (ISP), clearing house (CH) |

## Rules and Boundaries

- Select the protocol from the operation and endpoint roles, not from a vague product label.
- Keep each protocol's message identifiers, permissions, data types, profiles, status codes, and lifecycle rules within that protocol.
- OCAVS defines vehicle/fleet application management, including missions, supervision, telemetry, configuration, diagnostics, and safety events.
- OCAVM defines short-range awareness and cooperative coordination. Do not use it as a substitute for fleet mission management or platform commerce.
- OCAVI defines service and commercial exchanges between platforms. It does not define vehicle actuation or peer safety broadcasts.
- Read the selected protocol's scope, terminology, deployment, and profile rules before implementing an operation.
- Treat the normative specification tree as authoritative. Checklists and operations-design records provide planning context only.
- These repositories describe protocol contracts; do not assume they provide a runtime, SDK, or implementation.

## Common Pitfalls

- Applying a rule from one protocol to another because the names or payload concepts look similar.
- Choosing a profile without checking its dependencies and mandatory operations.
- Treating a repository's design record as more authoritative than the normative files.
- Assuming transport or deployment behavior that the selected protocol does not specify.
