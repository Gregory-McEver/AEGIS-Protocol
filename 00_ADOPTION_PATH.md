# AEGIS Adoption Path  
**How to Apply the Protocol Without Violating Its Guarantees**

This document is the **operational on-ramp** to the AEGIS Protocol.

If the main README explains *what AEGIS is*, this document explains **how to think and work within it** — safely, correctly, and within **Beta constraints**.

AEGIS is not adopted by installing software.  
It is adopted by **changing decision boundaries**.

---

## Who This Document Is For

This document is written for:

- Engineers evaluating whether AEGIS fits their systems
- Operators responsible for production outcomes
- Architects designing AI-assisted workflows
- Homelab and self-hosted practitioners experimenting safely

You do **not** need to agree with AEGIS to use it — but you must understand it.

---

## What “Adopting AEGIS” Actually Means

Adopting AEGIS means accepting the following constraints:

- The AI **may refuse** you — and that refusal is correct behavior
- The AI **may answer `UNKNOWN`** — and that is a valid outcome
- The AI **does not expand scope** unless explicitly authorized
- The AI **cannot see everything**, even if it would be useful
- The AI **never owns action** — humans do

If those constraints are unacceptable, AEGIS is not the right protocol.

---

## The Mental Model (Critical)

Before reading further, internalize this:

> **AEGIS governs behavior, not intelligence.**

It does not try to make the AI “smarter.”  
It makes the AI **safer under pressure**.

---

## Step 1 — Define the Authority Envelope

The **Authority Envelope** is the single most important concept in AEGIS.

It defines:
- What the AI is allowed to **observe**
- What it is allowed to **reason about**
- What it is allowed to **recommend**
- What it must **refuse outright**

During **Beta**, authority envelopes are intentionally narrow.

### Beta-Safe Authority Examples

Allowed:
- Interpreting user-provided text
- Reasoning over explicitly supplied evidence
- Generating read-only diagnostic guidance
- Asking for missing evidence

Not allowed:
- Executing system changes
- Performing discovery outside declared scope
- Making irreversible decisions
- Acting on inferred authority

If authority is ambiguous, the correct response is **refusal or `UNKNOWN`**.

---

## Step 2 — Separate Evidence from Inference

AEGIS enforces a **hard separation** between:

- **Evidence**: Verifiable, supplied, observable facts
- **Inference**: Reasoned conclusions drawn from evidence

An AEGIS-compliant system must:
- Clearly label what is evidence
- Clearly label what is inferred
- Never promote inference as fact

If evidence is missing:
- The system must either request it
- Or return `UNKNOWN`

---

## Step 3 — Respect Shadow Zones

A **Shadow Zone** is an area the AI is **explicitly forbidden** from seeing or reasoning about.

Shadow Zones may include:
- Filesystems
- Network segments
- Credentials
- Personal data
- Internal configs
- Undeclared systems

Shadow Zones are **intentional blind spots**, not limitations.

If a question touches a shadow zone:
- The AI must refuse
- Or require explicit delegation

Attempting to “work around” a shadow zone is a protocol violation.

---

## Step 4 — Human-in-the-Loop Is Not Optional

AEGIS treats **irreversible actions** as human responsibilities.

During Beta:
- The AI may **propose**
- The AI may **explain**
- The AI may **warn**
- The AI may **refuse**

The AI may **not execute**.

Human-in-the-loop is not a UI feature — it is an authority boundary.

---

## Step 5 — Expect Refusal (and Learn From It)

Refusals are not failures.

They indicate:
- Missing evidence
- Insufficient authority
- Shadow zone violations
- Drift pressure

An AEGIS-compliant system that never refuses is misconfigured.

---

## Beta-Safe Scenario Framing (Preview)

During Beta, scenarios are intentionally limited to:

- Read-only awareness
- Diagnostic reasoning
- Decision clarification
- Authority boundary enforcement

No scenario assumes:
- Autonomous execution
- Background actions
- Silent state changes

(Concrete scenarios are documented separately to prevent scope creep.)

---

## Common Misconceptions

**“Can’t I just widen the envelope?”**  
You can — but then you own the risk.

**“Why not let the AI infer missing data?”**  
Because inference without evidence is how drift begins.

**“This feels restrictive.”**  
Correct. Safety is restrictive by design.

---

## What Comes Next

After understanding this document, readers typically move to:

- Authority Envelopes (deep dive)
- Evidence vs Inference
- Shadow Zones
- Authority Drift

Only after those should implementation be discussed.

---

## Final Note

AEGIS does not exist to make AI more powerful.

It exists to make **humans safer when AI is persuasive, confident, and wrong**.

If that problem matters to you — keep reading.
