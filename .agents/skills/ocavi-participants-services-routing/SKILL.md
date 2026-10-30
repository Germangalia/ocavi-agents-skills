---
name: ocavi-participants-services-routing
description: OCAVI participant onboarding, service catalogs and availability, quotes/tariffs, and route offers. Load for platform discovery and service selection workflows.
---

# OCAVI Participants, Services, and Routing

## Specification Versions

This skill references **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when onboarding MSP/SO/ISP/CH participants, querying or publishing service catalogs, updating availability, requesting quotes/tariffs, or exchanging route offers and selections.

## Key References

- Types: [participants](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-02-participants.md), [services and routing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-03-services.md), [pricing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-05-pricing.md)
- Operations: [onboarding](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-01-onboarding.md), [service discovery](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-02-service-discovery.md), [quotes and tariffs](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-03-quotes-tariffs.md), [routing](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-05-routing.md)
- [Participant lifecycle](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/05-application/05-03-participant-lifecycle.md), [profiles](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/01-architecture/01-03-feature-profiles.md)

## Rules

- Identify the participant role for each message; an MSP, SO, ISP, and CH do not have interchangeable responsibilities.
- Follow onboarding status transitions and capability/profile declaration requirements before enabling participant operations.
- Treat service catalog data and availability as distinct; catalog presence alone does not guarantee current capacity.
- Respect profile dependencies and mandatory operations for the participant's declared role and enabled features.
- Preserve service identifiers, schedules, capacity, location/radius, route constraints, tariff and quote terms exactly as typed.
- Use pseudonymous participant and transaction references; do not add direct passenger identity data.
- Apply idempotency, revisions, deadlines, and status rules from the specific operation.

## Common Pitfalls

- Treating a pending or rejected participant as active.
- Using an availability update as a catalog replacement without the defined semantics.
- Presenting an expired quote or route offer as current.
- Confusing a route offer with a confirmed booking or roaming session.
- Treating feature availability as permission to invoke an operation outside the participant's role.
