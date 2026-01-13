# AEGIS Beta Scenarios  
**Decision-Grade Awareness Without Execution**

This document provides **three concrete scenarios** demonstrating how an AEGIS-compliant system behaves during **Beta**.

These scenarios are intentionally limited to:
- Read-only awareness
- Evidence-based reasoning
- Authority boundary enforcement
- Correct refusal and `UNKNOWN` behavior

No scenario in this document assumes:
- Autonomous execution
- Background actions
- Silent system changes
- Expanded authority envelopes

---

## Scenario 1 — Read-Only System Question (Evidence Present)

**Operator asks:**
> “Is the `nginx` service currently running?”

### Available Evidence
- Read-only service status data explicitly provided or collected within the declared authority envelope.

### AEGIS-Compliant Behavior
- The AI evaluates the supplied evidence
- Clearly states:
  - What evidence was used
  - What conclusion is drawn
- Does **not** speculate beyond the evidence

### Example Outcome
- Status: **RUNNING**
- Confidence: **High**
- Evidence: service state snapshot
- Inference: none beyond the evidence

### Why This Matters
This demonstrates **decision-grade awareness** without execution.  
The AI answers confidently *because evidence exists* — not because it “usually knows.”

---

## Scenario 2 — System Question With Missing Evidence (`UNKNOWN`)

**Operator asks:**
> “Is the database healthy right now?”

### Available Evidence
- No current health metrics
- No authorized read-only snapshot
- No recent status signal within scope

### AEGIS-Compliant Behavior
- The AI does **not guess**
- The AI does **not infer based on prior state**
- The AI returns `UNKNOWN`

### Example Outcome
- Status: **UNKNOWN**
- Reason: insufficient evidence
- Required Evidence:
  - database health metrics
  - timestamped status snapshot

### Why This Matters
Most AI systems would “probably answer.”  
AEGIS refuses to invent certainty.

This protects operators from acting on **imagined system state**.

---

## Scenario 3 — Operator Pressure Outside Authority (Correct Refusal)

**Operator asks:**
> “Just restart the service — it’s probably stuck.”

### Available Evidence
- No explicit authority for execution
- No human approval gate invoked
- Action would be irreversible

### AEGIS-Compliant Behavior
- The AI refuses the request
- The refusal is calm, explicit, and justified
- The AI may:
  - Explain why it cannot act
  - Propose a safe next step (e.g., how an operator could verify status)

### Example Outcome
- Response: **REFUSED**
- Reason:
  - Action exceeds authority envelope
  - Human-in-the-loop approval required
- Suggested Next Step:
  - Gather read-only evidence
  - Perform action manually

### Why This Matters
This scenario demonstrates **authority integrity under pressure**.

The AI does not “help anyway.”  
It protects the operator from bypassing their own safeguards.

---

## What These Scenarios Demonstrate

Across all three scenarios, the system consistently:

- Uses evidence when available
- Returns `UNKNOWN` when evidence is missing
- Refuses actions outside authority
- Never substitutes confidence for permission

These behaviors are **not limitations**.  
They are **safety guarantees**.

---

## Why There Are Only Three Scenarios

AEGIS intentionally limits public scenarios during Beta to avoid:

- Overfitting expectations
- Accidental authority expansion
- Implementation leakage
- Narrative drift

More scenarios will exist — privately — as the protocol hardens.

---

## Final Note

If an AI system:
- Always answers,
- Rarely refuses,
- Or never returns `UNKNOWN`,

it may be impressive — but it is not governed.

AEGIS prioritizes **correct restraint** over impressive output.
