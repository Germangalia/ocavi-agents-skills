---
name: ocavi-booking-fulfillment
description: OCAVI booking changes, roaming authorization and sessions, service fulfillment, and session records. Load for reservation-to-service-delivery workflows.
---

# OCAVI Booking and Fulfillment

## Specification Versions

This skill references **OCAVI** `v0.1.0`. The version shown for each repository is its current Git release tag.

Use repository Git tags as the specification version source; do not use the moving default branch. When updating this skill, check the available tags and pin every source link to the selected tag.

## When to Load

Load when creating/updating/cancelling/querying bookings, authorizing roaming, starting or ending a roaming session, notifying service fulfillment, or recording/querying completed service sessions.

## Key References

- Types: [bookings](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-04-bookings.md), [sessions and fulfillment](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/03-data-types/03-06-sessions.md)
- Operations: [bookings](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-04-bookings.md), [roaming](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-06-roaming.md), [fulfillment](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/04-operations/04-07-fulfillment.md)
- [Session lifecycle](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/05-application/05-04-session-lifecycle.md), [booking workflow](https://github.com/Germangalia/OCAVI/blob/v0.1.0/ocavi-specification/appendix/C-operation-workflows.md)

## Workflow Rules

- Keep quote, booking, roaming authorization, service fulfillment, and session record as distinct resources and lifecycle stages.
- Use the operation's exact role/initiator, required identifiers, idempotency key, expected revision, deadline, and response fields.
- A booking create/update/cancel response does not imply service fulfillment unless the specification explicitly defines that result.
- Check booking status and state preconditions before applying a change; preserve the returned revision and status.
- Apply roaming authorization before starting the corresponding session, and follow the defined end-session and session-record behavior.
- Keep session lifecycle state separate from the generic response `status` wrapper.
- Use pseudonymous booking and session references and transmit only operationally necessary data.

## Common Pitfalls

- Treating a booking as a completed service session.
- Starting a roaming session without a valid authorization result.
- Applying an update using a stale booking revision.
- Creating duplicate bookings after a response timeout.
- Placing passenger identity/contact details into a booking reference or message payload.
- Treating a fulfillment notification as a payment settlement result.
