---
name: ocva-spec-authoring
description: Normative document ownership, requirement language, repository conventions, examples, checklists, and release discipline for OCAVS, OCAVM, and OCAVI.
---

# OCVA Specification Authoring

## Specification Versions

This skill references **OCAVS** `v0.1.0`, **OCAVM** `v0.1.0`, **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when drafting or editing normative specification files, message examples, operation designs, documentation checklists, release notes, or implementation guidance for any of the three protocol repositories.

## Key References

- Each repository's `README.md`, `*-DOCUMENTATION-CHECKLIST.md`, and `*-OPERATIONS-DESIGN.md` at [OCAVS](https://github.com/Germangalia/OCAVS/tree/v0.1.0), [OCAVM](https://github.com/Germangalia/OCAVM/tree/v0.1.0), and [OCAVI](https://github.com/Germangalia/OCAVI/tree/v0.1.0)
- Each repository's `00-foundation/00-02-terminology-and-conventions.md` and the normative file that owns the edited behavior.
- Each repository's `appendix/B-message-examples.md` and `appendix/D-limits-defaults.md` when examples or global constraints are involved.

## Authority and Editing Rules

- Only manually authored Markdown in the protocol's `*-specification/` tree is normative, as described by that repository's README.
- Root checklists are tracking material. Operations-design files are non-normative design records. If either differs from the normative specification, preserve the normative behavior and report the discrepancy.
- Find the single normative owner for a fact before editing. Avoid duplicate or conflicting definitions across files.
- Preserve visible document metadata, numbering, exact requirement strength, payload field names/types/cardinality, operation identifiers, permission names, status codes, and version values.
- Keep examples consistent with declared types and operation contracts. Do not let an example silently introduce a new rule.
- Check all dependent documents when changing a type, enum, operation, profile, state transition, limit, or status mapping.
- A released semantic contract is versioned and immutable under the repository's release rules. Do not silently revise an existing released version.
- Do not invent missing normative behavior. Mark the gap and identify the decision owner or required clarification.

## Review Checklist

- Does the edited file own the behavior being changed?
- Are request/response pairs, field cardinality, status outcomes, and lifecycle transitions internally consistent?
- Are cross-referenced types and enums owned by the expected data-type document?
- Are profile dependencies and role requirements preserved?
- Are examples valid and representative of the current normative contract?
- Are version declarations and repository-specific editorial constraints consistent?
- Are checklists updated as tracking artifacts without being presented as normative authority?

## Common Pitfalls

- Editing the design record while leaving the normative owner unchanged.
- Duplicating the same normative fact in multiple documents.
- Changing a field/type name in one operation but not in its type owner or examples.
- Treating a draft checklist or a root-level note as a protocol requirement.
- Making a semantic change without following the repository's version/release process.
- Adding a plausible behavior that has no normative source.
