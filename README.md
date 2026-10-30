# OCAVI Agents & Skills

[![skills.sh](https://skills.sh/b/Germangalia/ocavi-agents-skills)](https://skills.sh/Germangalia/ocavi-agents-skills)

A reusable knowledge base for AI agents working with the **Open Cooperative Vehicle Architecture (OCVA)** protocols, with focused coverage of **OCAVI** platform-to-platform interoperability.

This repository contains agent instructions and reusable skills for designing, implementing, integrating, documenting, and assessing OCVA protocol behavior. It does not contain a protocol runtime or application implementation. The normative specifications remain authoritative.

The three related protocols covered by the shared OCVA skills are:

- **OCAVS** — vehicle-to-server application and fleet/device management.
- **OCAVM** — short-range vehicle-to-vehicle and vehicle-to-infrastructure awareness and coordination.
- **OCAVI** — platform-to-platform service interoperability.

## Repository structure

```text
.agents/
├── agent/          # Role-based agent instructions (AGENT.md)
└── skills/         # Reusable protocol knowledge (SKILL.md)

README.md
skills             # Registry discovery pointer to .agents/skills
skills-lock.json   # Skills CLI lock file, when populated
```

## Skills

Skills are focused knowledge units that agents can load as needed.

| Skill | Coverage |
|---|---|
| `ocva-foundation` | Scope, terminology, roles, deployment, profiles, and boundaries across OCAVS, OCAVM, and OCAVI |
| `ocva-data-types` | Canonical scalar, object, enum, time, unit, identity, and geospatial representations |
| `ocva-message-semantics` | Request/response processing, idempotency, revisions, ordering, deadlines, and lifecycles |
| `ocva-security-privacy` | Validation, authorization, privacy, secure-connectivity assumptions, and external-transfer constraints |
| `ocva-conformance` | Conformance classes, status catalogs, state-machine requirements, examples, limits, and evidence |
| `ocva-spec-authoring` | Normative ownership, requirement language, examples, repository conventions, and release discipline |
| `ocavi-participants-services-routing` | OCAVI participant onboarding, service catalogs and availability, quotes/tariffs, and route offers |
| `ocavi-booking-fulfillment` | OCAVI booking changes, roaming authorization and sessions, fulfillment, and session records |
| `ocavi-commerce-settlement` | OCAVI quotes, tariffs, invoices, tokenized payments, settlement, reconciliation, and disputes |

**Total: 9 skills.** The `ocva-conformance/ocva-data-types/` path is a compatibility copy of `ocva-data-types`, not an additional skill.

## Agents

Agent definitions combine skills into task-focused responsibilities and outputs.

| Agent | Role |
|---|---|
| `protocol-architect` | Selects protocols, roles, profiles, normative owners, and deployment boundaries |
| `state-contract-engineer` | Designs typed message contracts, validators, idempotency, ordering, and state transitions |
| `security-privacy-engineer` | Reviews validation, authorization, privacy, and sensitive-data handling |
| `integration-specialist` | Designs and troubleshoots handoffs across OCAVS, OCAVM, and OCAVI |
| `ocavi-interoperability-developer` | Implements and reviews OCAVI onboarding, discovery, booking, fulfillment, and commerce workflows |
| `conformance-test-engineer` | Builds traceable positive, negative, lifecycle, security, and recovery conformance cases |
| `documentation-release-writer` | Authors and reviews protocol documentation, examples, and release materials |

**Total: 7 role-based agents.** Agent files are under `.agents/agent/`.

Some agent instructions list contextual skill identifiers for protocol areas that are not included in this checkout. Those references describe possible future or externally supplied skills; only the nine skills listed above are available locally through this repository.

## Using the knowledge base

1. Identify the protocol, operation, endpoint roles, profile, and specification version relevant to the task.
2. Load the matching agent instructions from `.agents/agent/` when a specialized role is useful.
3. Load the relevant skills from `.agents/skills/`. For cross-protocol work, start with `ocva-foundation` and add the applicable shared skills.
4. Follow the selected protocol's version-pinned normative specification for operation and type definitions.
5. Preserve protocol boundaries and report gaps instead of inventing behavior that the specification does not define.

For OCAVI work, select participant/service routing, booking/fulfillment, or commerce/settlement skills according to the workflow. For cross-protocol work, use the shared foundation, data-type, message-semantics, security, and conformance guidance as applicable.

The skills currently reference specification version **v0.1.0**. Resolve versions from the source repositories' Git release tags and use version-pinned links when consulting normative requirements. Normative specification files are authoritative; checklists and operation-design records are planning material.

## Installation

Install all available skills with the Skills CLI:

```bash
npx skills add Germangalia/ocavi-agents-skills
```

List skills available from the repository without installing them:

```bash
npx skills add Germangalia/ocavi-agents-skills --list
```

Install one skill by name:

```bash
npx skills add Germangalia/ocavi-agents-skills --skill ocavi-booking-fulfillment
```

Replace `ocavi-booking-fulfillment` with any skill name from the table above.

Browse the repository on [skills.sh](https://skills.sh/Germangalia/ocavi-agents-skills).

### Local repository usage

```bash
git clone https://github.com/Germangalia/ocavi-agents-skills.git
cd ocavi-agents-skills
```

Configure your agent runtime to load skills from `.agents/skills/` and, if supported, role instructions from `.agents/agent/`. The root-level `skills` pointer is intended to expose `.agents/skills/` to registry discovery tools.

## Design principles

- **Protocol-first architecture:** Keep vehicle/fleet management, peer coordination, and platform-service behavior within their proper protocol boundaries.
- **Modular knowledge:** Compose focused skills according to the task.
- **Version-pinned references:** Consult normative specification sources at identifiable release tags.
- **Data integrity:** Preserve exact field names, types, status values, permissions, and lifecycle rules.
- **Safety and privacy:** Handle vehicle, peer, service, and payment data according to the relevant protocol constraints.
- **Explicit gaps:** Identify unspecified behavior and cross-protocol mapping gaps instead of inventing requirements.
- **Reusable roles:** Organize specialized agent instructions around clear responsibilities and outputs.

## Current scope

This repository currently contains **9 skills** and **7 role-based agent definitions**. The skills provide shared OCVA guidance and focused OCAVI workflow coverage. OCAVS and OCAVM are represented in the shared cross-protocol skills and agent references; this checkout does not include dedicated OCAVS- or OCAVM-specific skills.

## License

No license is currently declared in this repository.
