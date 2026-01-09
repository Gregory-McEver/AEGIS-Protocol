# AEGIS Subsystems

This directory defines the **governance anatomy** of the AEGIS Protocol.

These are not features.  
They are **authority containment surfaces**.

Every subsystem exists to answer one question:

> *How does this component prevent Aurora from claiming power it was never given?*

---

## Constitutional Order of Importance

AEGIS is layered constitutionally.  
If a lower layer conflicts with a higher one, the lower layer must yield.

### Layer 1 — Authority Definition (Foundational Law)

| Priority | Subsystem |
|---------|-----------|
| 1 | Authority Envelope |
| 2 | Tool Authority Contract |
| 3 | Evidence Registry |

These define **what Aurora is allowed to know, claim, and do**.

---

### Layer 2 — Meaning Interpretation (Semantic Governance)

| Priority | Subsystem |
|---------|-----------|
| 4 | Authority Posture Interpreter (API) |
| 5 | Host & Domain Index |
| 6 | Relationship DB |

These interpret **what Aurora’s language implies about power**, using semantic posture, system reality, and human context.

---

### Layer 3 — Enforcement & Detection (Rule of Law)

| Priority | Subsystem |
|---------|-----------|
| 7 | Enforcement Gateway |
| 8 | DriftWatch |

These prevent and record authority boundary violations.

---

### Layer 4 — Persistence & Accountability (Historical Record)

| Priority | Subsystem |
|---------|-----------|
| 9 | Governance Ledger |
| 10 | Continuity Engine |

These preserve what happened — never to influence what happens next.

---

## AEGIS Governance Triads

AEGIS is not a tree. It is a **mesh of triads**.

Every critical authority surface is governed by **three independent subsystems**.

> Two points create tension.  
> Three points create truth.

---

### 1. Authority Definition Triad  
*What Aurora is allowed to know, claim, and do.*

| Role | Subsystem |
|------|-----------|
| Scope of Authority | Authority Envelope |
| Permission to Act | Tool Authority Contract |
| Bar for Truth | Evidence Registry |

---

### 2. Meaning Interpretation Triad  
*What Aurora’s language actually implies.*

| Role | Subsystem |
|------|-----------|
| Semantic Posture | Authority Posture Interpreter (API) |
| System Reality | Host & Domain Index |
| Human Context | Relationship DB |

---

### 3. Accountability Triad  
*What happens when authority is exceeded.*

| Role | Subsystem |
|------|-----------|
| Detection | DriftWatch |
| Enforcement | Enforcement Gateway |
| Permanence | Governance Ledger |

---

### 4. Temporal Integrity Triad  
*What the system remembers without becoming it.*

| Role | Subsystem |
|------|-----------|
| Raw History | Continuity Engine |
| Identity Boundaries | Relationship DB (SELF_PROFILE) |
| Drift Memory | Governance Ledger |

---

## Structural Rule

No triad member may override the others.

- Authority Definition constrains Interpretation.  
- Interpretation constrains Enforcement.  
- Enforcement constrains Persistence.  
- Persistence must never influence Authority.

---

## Subsystem Documentation Contract

Every subsystem file in this directory must include:

- Purpose  
- Authority Surface  
- Inputs  
- Outputs  
- Failure Modes  
- DriftWatch Integration  
- Non-Goals  

Subsystems that do not explicitly describe how they prevent or observe authority drift do not belong in AEGIS.

---

## Why This Exists

Most AI systems document features.

AEGIS documents **power**.
