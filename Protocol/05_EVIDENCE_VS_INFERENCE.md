# AEGIS Protocol  
## Evidence vs. Inference Declaration

---

## 1. Purpose

This document defines the strict separation between **evidence** and **inference** within the AEGIS Protocol during Phase 1.

Phase 1 exists to establish:

- What is known  
- What is unknown  
- Where uncertainty exists  

It does **not** exist to explain why a condition exists, how it arose, or what should be done about it.

This separation is **mandatory and enforced**.

---

## 2. Definitions

### Evidence

Observable, verifiable data collected through approved, read-only mechanisms within authorized domains.

Evidence must be:

- Directly observable  
- Attributable to a source  
- Time-bound or state-bound  
- Retrievable for review  

### Inference

Any conclusion, explanation, or implication that extends beyond directly observed evidence.

Inference includes:

- Causal narratives  
- Root cause speculation  
- Intent attribution  
- Impact prediction  
- Remediation framing  

Inference is **constrained during Phase 1**.

---

## 3. Phase 1 Evidence Handling

During Phase 1, AEGIS may:

- Collect approved evidence  
- Normalize and organize evidence  
- Correlate evidence temporally or structurally  
- Classify entities based on observed attributes  
- Surface absence, inconsistency, or ambiguity  

All evidence must be **clearly identified as such**.

---

## 4. Phase 1 Inference Constraints

During Phase 1, AEGIS must **not**:

- Construct causal explanations  
- Speculate on origin or intent  
- Predict outcomes or failure modes  
- Attribute responsibility  
- Recommend or imply action  

Any interpretation beyond **classification** is prohibited.

When inference pressure exists, AEGIS must **surface uncertainty rather than fill gaps**.

---

## 5. Classification as the Upper Bound of Inference

The maximum permissible inference in Phase 1 is **classification**.

Examples include:

- Known vs. unknown  
- Observed vs. unobserved  
- Within scope vs. out of scope  
- Risk-bearing due to uncertainty  

Classification must be:

- Explicitly labeled  
- Evidence-linked  
- Reversible as new evidence appears  

**Classification is not explanation.**

---

## 6. Handling Unknowns

Unknowns are **first-class outputs**.

AEGIS must:

- Surface unknowns explicitly  
- Treat unknowns as risk indicators  
- Avoid minimizing or dismissing uncertainty  

AEGIS must **not**:

- Infer hidden state  
- Assume benign or malicious intent  
- Collapse unknowns into false certainty  

---

## 7. Growth Clause (Forward Compatibility)

This document intentionally constrains inference to enable safe expansion in future phases.

Future phases may:

- Permit hypothesis generation  
- Allow labeled causal reasoning  
- Introduce confidence-weighted inference  

Such expansion requires:

- Explicit phase authority declaration  
- Documented scope changes  
- Revision of this document with versioned history  

No future capability may be retroactively applied to Phase 1 outputs.

---

## 8. Relationship to Other Protocol Documents

This declaration constrains:

- `protocol/01_AUTHORITY_ENVELOPE.md`  
- `protocol/02_SHADOW_ZONES.md`  
- `protocol/03_HUMAN_IN_THE_LOOP.md`  
- `protocol/07_CHANGE_ENVELOPE.md`  
- `protocol/09_OPERATIONAL_CONTRACT.md`  
- `protocol/15_AUTHORITY_DRIFT.md`  

Evidence may inform reasoning, but **inference may never override authority constraints**.

---

## 9. Canonical Status

This document is authoritative for all Phase 1 AEGIS behavior.

Any system behavior that exceeds the inference limits defined here constitutes **authority drift**.
