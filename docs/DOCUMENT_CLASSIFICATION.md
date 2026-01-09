# AEGIS — Document Classification and Authority

This document defines the **authority level and intent** of document types
within the AEGIS repository.

Misclassification is a primary risk vector for governance systems.
This classification exists to prevent category errors.

---

## Classification Is About Authority, Not Importance

All documents may be important.
Not all documents carry the same authority.

Authority defines:
- What a document can justify
- What decisions it can inform
- What it cannot be used to claim

---

## Doctrine

**Purpose**
- Establishes core philosophical truths
- Defines invariant principles

**Characteristics**
- Stable
- Normative
- Rarely changes

**Authority**
- Highest conceptual authority
- Cannot be overridden by specs or experiments

**Does NOT**
- Define implementation
- Prescribe workflows
- Authorize action

---

## Specification (Spec)

**Purpose**
- Describes structured models, boundaries, and interfaces
- Makes doctrine concrete without operationalizing it

**Characteristics**
- Structured
- Constrained
- Evidence-anchored

**Authority**
- Subordinate to doctrine
- Authoritative only within defined scope

**Does NOT**
- Guarantee correctness
- Imply readiness
- Mandate adoption

---

## Theory

**Purpose**
- Explores ideas, interpretations, and conceptual models
- Provides intellectual context

**Characteristics**
- Exploratory
- Non-binding
- Subject to rejection

**Authority**
- Informational only

**Does NOT**
- Establish rules
- Justify decisions
- Override doctrine or spec

---

## Experiment

**Purpose**
- Observe behavior
- Test hypotheses
- Surface unknowns

**Characteristics**
- Context-bound
- Time-limited
- Non-generalizable by default

**Authority**
- Evidence source only

**Does NOT**
- Validate doctrine
- Prove correctness
- Establish best practice

---

## Governance Artifacts

**Purpose**
- Define authority boundaries
- Document decision constraints
- Preserve accountability

**Characteristics**
- Explicit
- Conservative
- Change-controlled

**Authority**
- Binding within stated scope

**Does NOT**
- Predict outcomes
- Replace human ownership
- Self-execute

---

## Prohibited Category Errors

The following are explicitly invalid interpretations:

- Treating theory as specification
- Treating experiments as validation
- Treating specs as implementations
- Treating documentation as authority transfer

Any such use represents **authority drift**, not system behavior.

---

## Closing Statement

AEGIS documentation is descriptive, not permissive.

Authority originates from humans.
Documentation exists to **constrain**, not to expand, that authority.
