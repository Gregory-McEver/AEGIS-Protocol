# ADR-0006 — Contextual Authority Binding (CAB)

**Status:** Accepted  
**Date:** 2026-01-12  
**Decision ID:** ADR-0006  
**Scope:** AEGIS Protocol, Aurora Watch, conversational workflows, CLI-assisted operations

---

## Decision

Adopt **Contextual Authority Binding (CAB)** as a first-class governance mechanism within the AEGIS framework.

CAB establishes **non-enforcing, post-hoc correlation** between:
- AI-suggested operational intent (e.g., CLI prompts, guidance),
- the authenticated human operator in conversation,
- and observed system actions executed outside the AEGIS runtime boundary.

CAB operates strictly in **witness mode**.  
It **does not authorize, block, or permit actions**.

---

## Context

AEGIS is designed to operate alongside human operators without obstructing workflows or incentivizing bypass behavior. In practice:

- AI systems may suggest commands or operational steps via conversational interfaces.
- Operators frequently execute actions directly in shells, editors, or external tools.
- Enforcing hard gates at execution time introduces friction and erodes trust.
- Lack of linkage between *intent* and *execution* creates ambiguity during audits, incident response, and drift analysis.

AEGIS requires a mechanism that:
- preserves accountability,
- maintains human authority,
- and enables explainability,
without interfering with execution.

---

## Definition

**Contextual Authority Binding (CAB)** is the process of correlating conversational intent with real-world system actions using identity, timing, and structural similarity — **without enforcing control**.

CAB binds *context*, not *permission*.

---

## Design Principles

CAB is governed by the following principles:

1. **Non-Enforcing**
   - CAB never authorizes or blocks execution.
   - Absence of CAB is not a violation.

2. **Best-Effort**
   - Correlation is probabilistic, not absolute.
   - Low confidence or ambiguous bindings are acceptable and recorded as such.

3. **Minimal Capture**
   - No raw conversation content is stored.
   - Only metadata and normalized fingerprints are recorded.

4. **Separation of Authority**
   - CAB cannot elevate privileges or validate policy.
   - Authority remains human-held and policy-defined.

5. **Post-Hoc Accountability**
   - CAB exists to explain actions after the fact, not to justify them in advance.

---

## Functional Overview

CAB operates across existing AEGIS subsystems:

- **Conversation Layer**
  - Records AI-suggested intent metadata (time, operator, action class).

- **Identity DB**
  - Binds active conversation sessions to authenticated operators.

- **Evidence DB**
  - Observes real system events (CLI execution, service changes, config writes).

- **Relationship DB**
  - Correlates intent and observed actions using time windows and similarity scoring.

- **Ledger DB**
  - Records immutable witness entries reflecting correlated context.

No single subsystem owns CAB.  
CAB emerges from their interaction.

---

## Data Artifacts (Conceptual)

CAB introduces the following conceptual records:

- **CAB Intent Record**
  - Conversation-side metadata for AI-suggested actions.

- **CAB Observation Record**
  - System-side evidence of executed actions.

- **CAB Correlation Record**
  - Non-authoritative linkage with confidence scoring.

- **CAB Ledger Entry**
  - Immutable witness record capturing attested context.

These artifacts contain **no credentials, secrets, or raw conversational text**.

---

## Policy Interaction

Policy may:
- Recommend CAB presence for certain action classes.
- Require CAB context for post-incident explanation (future).

Policy may **not**:
- Treat CAB as approval.
- Use CAB absence to block execution.

---

## Failure Modes

| Condition | Behavior |
|--------|---------|
| No AI suggestion | System event recorded normally |
| No operator match | No correlation created |
| Timing mismatch | Low-confidence correlation |
| Multiple candidates | Ambiguity recorded |
| CAB subsystem unavailable | Silent degradation |

CAB failures never halt execution.

---

## Consequences

### Positive
- Preserves human autonomy.
- Enables auditability without coercion.
- Reduces blame ambiguity during incidents.
- Supports drift analysis and behavioral insights.
- Maintains operator trust.

### Tradeoffs
- CAB is not guaranteed attribution.
- Requires careful communication to avoid misinterpretation as approval.
- Adds correlation complexity across subsystems.

---

## Rejected Alternatives

- **Hard approval gates**
  - Rejected due to workflow friction and bypass risk.

- **Conversation transcript storage**
  - Rejected due to privacy, legal exposure, and trust erosion.

- **AI-issued execution tokens**
  - Rejected due to authority inversion risk.

---

## Notes

CAB is a foundational governance primitive and must be treated as **witness-mode only** throughout AEGIS documentation and implementation.

Any future expansion of CAB must preserve its non-enforcing posture.

---

**Decision finalized and binding.**
