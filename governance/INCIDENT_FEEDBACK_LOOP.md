# Incident Feedback Loop

This document defines how AEGIS converts incidents into permanent governance improvements.

An incident that does not change the protocol is a failure twice.

---

## When This Loop Triggers

This process must run after:

- Any D2+ Authority Drift event
- Any system action requiring human override
- Any incident involving unbounded inference
- Any event that violates the Authority Envelope

---

## Mandatory Outputs

Every qualifying incident must produce:

| Artifact | Description |
|--------|-------------|
| Incident Report | What happened |
| Root Cause Analysis | Why it happened |
| Envelope Delta Proposal | What authority boundaries must change |
| Risk Tier Reclassification | Does this system now carry higher risk |
| Governance Amendment | What rule must be updated to prevent recurrence |

---

## Amendment Rules

- No incident is considered closed until at least one governance document is updated.
- All amendments require human approval.
- All updates must reference the originating incident ID.

---

## Drift Immunization

Every amendment must explicitly state:

> What future behavior this change prevents.
