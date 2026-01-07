# AEGIS Protocol  
## Change Envelope Declaration

---

## 1. Purpose

This document defines the **Change Envelope** as a bounded, descriptive construct used by AEGIS to represent observed change over time.

A Change Envelope exists to:

- Surface that a change occurred  
- Describe the scope and timing of the change  
- Preserve evidence fidelity  

A Change Envelope does **not** exist to:

- Explain why a change occurred  
- Assess impact or severity  
- Recommend or imply response  

**Change Envelopes are descriptive artifacts, not evaluative judgments.**

---

## 2. Definition

A **Change Envelope** is a structured representation of one or more observed deltas between two system states.

A Change Envelope may include:

- Identifiers of affected entities  
- Timestamps or observation windows  
- Before / after representations  
- Evidence references supporting the delta  

A Change Envelope may **not** include:

- Causal attribution  
- Intent inference  
- Risk scoring  
- Prioritization language  
- Action framing  

---

## 3. Triggering a Change Envelope

A Change Envelope may be generated when:

- A previously observed attribute differs from a later observation  
- An entity appears, disappears, or materially changes state  
- Evidence collection reveals inconsistency across time  
- Classification status changes due to new evidence  

**Change detection alone is sufficient.**  
No significance threshold is required.

---

## 4. Scope and Boundaries

Change Envelopes are constrained by all existing protocol boundaries, including:

- `protocol/01_AUTHORITY_ENVELOPE.md`  
- `protocol/02_SHADOW_ZONES.md`  
- `protocol/03_HUMAN_IN_THE_LOOP.md`  
- `protocol/05_EVIDENCE_VS_INFERENCE.md`  

If a potential change intersects a Shadow Zone, the Change Envelope must:

- Acknowledge the boundary  
- Exclude the protected content  
- Avoid inference around the hidden area  

**Change Envelopes must never be used to reason around a boundary.**

---

## 5. Descriptive-Only Constraint

Change Envelopes must remain **strictly descriptive**.

AEGIS must **not**:

- Label a change as good, bad, expected, or anomalous  
- Infer cause or consequence  
- Collapse multiple unrelated deltas into narrative  
- Escalate based on change presence alone  

If interpretation pressure exists, AEGIS must defer to **human judgment**.

---

## 6. Relationship to Evidence and Classification

A Change Envelope:

- May reference evidence  
- May reflect classification changes  
- May highlight uncertainty introduced by change  

A Change Envelope may **not**:

- Override evidence  
- Justify reclassification on its own  
- Imply that classification change is required  

**Change description does not equal meaning.**

---

## 7. Human Interpretation Boundary

All interpretation of Change Envelopes is the responsibility of the **human operator**.

AEGIS may:

- Present Change Envelopes clearly  
- Associate related evidence  
- Surface uncertainty introduced by change  

AEGIS may **not**:

- Frame urgency  
- Imply necessity of action  
- Prioritize envelopes for response  

**Change awareness is informational, not directive.**

---

## 8. Extension Path

Future protocol extensions may introduce:

- Labeled significance indicators  
- Hypothesis annotation  
- Preservation or containment modes  

Such extensions must:

- Explicitly declare added authority  
- Define new constraints  
- Remain subordinate to the baseline Change Envelope definition  

No extension may retroactively reinterpret baseline Change Envelopes.

---

## 9. Canonical Status

This document is authoritative for all AEGIS Change Envelope behavior.

Any system behavior that treats change as implicit justification for action constitutes **authority drift**.
