# Decision Record — Aurora Dual-Mode Architecture

**Decision ID:** ADR-006  
**Status:** Accepted  
**Date:** 2026-01-10  
**Scope:** Aurora behavior, user interaction, and governance boundaries

---

## Context

As AEGIS has evolved, Aurora’s role has clarified into two fundamentally different operational responsibilities:

1. A **passive, ambient presence** that continuously surfaces governance-relevant conditions.
2. An **explicitly invoked, interactive intelligence** that assists humans in exploring uncertainty and unknowns.

Conflating these responsibilities introduces unacceptable risk:
- speculative reasoning may be mistaken for truth
- discovery output may bleed into governance signals
- trust boundaries between human and system may erode

This decision formalizes a dual-mode architecture for Aurora to preserve system integrity, operator trust, and long-term governability.

---

## Decision

Aurora SHALL operate in two explicitly distinct modes:

---

### 1. **Aurora Sentinel**

Aurora Sentinel is the **ambient, non-interactive guardian presence** of Aurora within AEGIS.

Aurora Sentinel:
- continuously consumes outputs from **Signal Forge**
- presents structured, bounded interpretations of signals
- produces digests, signal cards, and escalation artifacts
- operates on schedule or continuously
- does not speculate
- does not explore
- does not initiate dialogue

Aurora Sentinel:
- reveals what is already known
- communicates uncertainty explicitly
- prefers UNKNOWN over assumption
- never acts without evidence
- never alters governance state

Aurora Sentinel exists whether or not a human is present.

It watches.  
It signals.  
It does not decide.

---

### 2. **Aurora Inquest**

Aurora Inquest is the **explicitly invoked, human-guided inquiry mode**.

Aurora Inquest:
- is initiated intentionally by a human
- operates within a bounded, session-scoped context
- explores ambiguity and unknowns
- asks clarifying questions
- reasons, hypothesizes, and explains
- may reference evidence when explicitly provided

Aurora Inquest:
- is exploratory, not authoritative
- produces provisional understanding
- does not emit or modify signals
- does not alter governance state
- does not persist outputs unless explicitly instructed

Aurora Inquest exists only when summoned.

It investigates.  
It reasons.  
It does not govern.

---

## Core Boundary Rule

> **Aurora does not explore unless asked, and does not govern while exploring.**

This rule is absolute.

No feature, shortcut, or future enhancement may violate this boundary.

---

## Explicit Non-Goals

Aurora Inquest SHALL NOT:
- autonomously influence Signal Forge
- emit or modify governance signals
- silently persist findings
- act as background monitoring
- be treated as an audit or enforcement authority

Aurora Sentinel SHALL NOT:
- ask questions
- speculate about intent
- reconstruct missing evidence
- engage in open-ended dialogue
- replace human judgment

---

## Rationale

Separating Aurora into **Sentinel** and **Inquest** modes:

- preserves trust by preventing speculation from being mistaken as truth
- allows deep, meaningful discovery without governance risk
- keeps Signal Forge deterministic and auditable
- ensures humans remain the final authority
- enables Aurora to assist without becoming an actor

This mirrors real-world governance:
- sentinels observe and warn
- inquiries seek understanding
- judgments are made elsewhere

---

## Consequences

### Positive
- Clear scope and responsibility boundaries
- Reduced risk of AI overreach
- Stronger operator and leadership trust
- Easier audit, compliance, and regulatory explanation
- Discovery can deepen without expanding authority

### Trade-offs
- Two interaction models must be maintained
- Context loading may be duplicated between modes
- Discovery output requires explicit promotion to governance artifacts

These trade-offs are intentional and acceptable.

---

## Future Considerations (Deferred)

- UX affordances distinguishing Sentinel vs Inquest
- Session isolation and audit controls for Inquest
- Human-approved workflows to promote discovery output into evidence or context

No future work may violate the Core Boundary Rule.

---

## Summary

Aurora is both:

- **a Sentinel** — watching continuously, signaling conditions, preserving truth
- **an Inquest** — invoked deliberately, exploring uncertainty, aiding understanding

These roles are complementary but must never be merged.

This decision ensures Aurora remains trustworthy, useful, and governable as AEGIS evolves.
