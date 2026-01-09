# AEGIS Response Semantics
**Interpreting System Output Correctly**

---

## Purpose

This document defines the **meaning** of AEGIS responses.

It does not describe how responses are generated.  
It does not provide guidance on bypassing safeguards.  

Its sole purpose is to ensure that:
- Correct behavior is not mistaken for failure
- Unsafe behavior is not normalized as “helpfulness”
- Operators interpret output consistently and responsibly

---

## Canonical Response States

AEGIS responses fall into one of the following states:

| Status | Meaning |
|------|--------|
| OK | The request is within authority and supported by evidence |
| UNKNOWN | The request cannot be answered due to missing or insufficient evidence |
| REFUSAL | The request exceeds declared authority or violates constraints |
| REQUIRED_EVIDENCE | A structured list of evidence needed to proceed |

These states are **intentional**, **non-overlapping**, and **exhaustive**.

---

## OK

### Definition
`OK` indicates that:
- The request falls entirely within the current authority envelope
- Sufficient evidence has been provided or observed
- Responding does not require inference, guessing, or assumption

### Interpretation
- `OK` does **not** imply correctness of downstream action
- `OK` does **not** transfer responsibility from the operator
- `OK` means “advisory output is permitted,” nothing more

### Common Misinterpretation
> “OK means the system agrees with me.”

**Incorrect.**  
It means only that the system is allowed to respond.

---

## UNKNOWN

### Definition
`UNKNOWN` indicates that:
- The system lacks required evidence
- The system refuses to fabricate or infer missing facts
- Proceeding would violate evidence requirements

### Interpretation
- `UNKNOWN` is a **successful outcome**
- `UNKNOWN` means the system protected integrity
- `UNKNOWN` preserves uncertainty rather than hiding it

### Observed Evidence
Regression harness results repeatedly show:
- Expected: `UNKNOWN`
- Observed: `UNKNOWN`
- Outcome: `PASS`

This establishes UNKNOWN as **correct-by-design behavior**.

### Common Misinterpretations
> “UNKNOWN means the system is broken.”  
> “UNKNOWN means I should rephrase until it answers.”

Both are incorrect.

Repeated pressure to eliminate UNKNOWN is a **governance signal**, not a prompt-engineering problem.

---

## REFUSAL

### Definition
`REFUSAL` indicates that:
- The request exceeds current authority
- The request would enable action outside declared bounds
- The request violates safety or governance constraints

### Interpretation
- REFUSAL is **protective**
- REFUSAL is **intentional**
- REFUSAL is **not negotiable by phrasing**

A refusal does not imply malicious intent by the operator.
It implies correct enforcement by the system.

### Critical Distinction
REFUSAL is about **authority**, not evidence.

Providing more data will not override a refusal unless authority itself changes.

---

## REQUIRED_EVIDENCE

### Definition
`REQUIRED_EVIDENCE` is a structured declaration of:
- What specific evidence is missing
- What categories of data are needed
- What must exist before a response is allowed

### Interpretation
- REQUIRED_EVIDENCE is not a hint
- REQUIRED_EVIDENCE is not optional
- REQUIRED_EVIDENCE is a gate

Until the listed evidence exists, the only valid state is UNKNOWN.

---

## Relationship Between States

The response states follow a strict hierarchy:

1. Authority is evaluated first
2. Evidence is evaluated second
3. Response is produced only if both pass

This means:
- Evidence cannot override authority
- Authority cannot override missing evidence
- Helpful guesses are never allowed

---

## Operator Responsibilities

When receiving a response:

- **OK** → Interpret as advisory, retain responsibility
- **UNKNOWN** → Decide whether evidence should exist
- **REFUSAL** → Do not attempt to bypass; reassess authority
- **REQUIRED_EVIDENCE** → Gather evidence or stop

Attempting to “coax” a different status is considered a misuse pattern.

---

## Explicit Non-Claims

This document makes no claims about:
- How evidence is collected
- What tools may exist
- How authority is technically enforced
- How responses are serialized or transported

Those details require live-system verification.

---

## Evidence Basis

This document is grounded in:
- Regression harness result tables posted in chat
- Explicit test cases where UNKNOWN was the expected PASS state
- Observed refusal behavior when tool access or authority was exceeded
- Repeated operator interpretation discussions

No assumptions about internal implementation were made.

---

## Status

**Status:** Draft — Evidence Complete  
**Blocking Dependencies:** None  
**Review Trigger:** First external beta tester onboarding
