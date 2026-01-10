# Design Veto — Windows as an AEGIS Host Platform

**Design Veto ID:** DV-001  
**Status:** Vetoed  
**Date:** 2026-01-10  
**Category:** Platform Architecture  
**Related Issue:** #38  

---

## Design Veto Statement

Running AEGIS on Microsoft Windows as a **host execution platform** is **explicitly vetoed by design**.

AEGIS SHALL NOT be installed, executed, or hosted on Windows.

AEGIS is architected to operate exclusively on a Linux-based system (Ubuntu) within a controlled **shadow-zone**, where evidence ingestion, normalization, governance logic, and analytics are executed under Linux-defined invariants.

This veto is architectural and intentional.

---

## Scope Clarification

This veto applies **only** to Windows as a **host or execution environment** for AEGIS.

This veto does **not** prohibit:
- ingesting evidence originating from Windows systems
- analyzing Windows-derived artifacts
- observing Windows environments indirectly

Windows is treated as an **observed surface**, not a **governing platform**.

---

## Design Context

AEGIS is not a general-purpose application.

It is a governance and evidence system whose correctness depends on:
- deterministic filesystem semantics
- stable permission and ownership models
- predictable process and service behavior
- auditable state transitions
- enforceable isolation boundaries

These properties are foundational to:
- the Observation Plane
- Signal Forge
- Aurora Sentinel
- evidence preservation and auditability

Windows as a host platform introduces abstraction layers and behavioral variability that conflict with these invariants.

---

## Vetoed Designs

The following designs are explicitly vetoed:

- Installing AEGIS on Windows
- Executing any AEGIS component on Windows
- Treating Windows as a first-class runtime for Signal Forge, Sentinel, or Inquest
- Performing primary evidence normalization or governance processing on Windows
- Designing AEGIS features that assume Windows-native execution semantics

These designs violate shadow-zone isolation and undermine evidence determinism.

---

## Approved Design

AEGIS SHALL:

- run on a dedicated Linux system (Ubuntu)
- operate within an isolated shadow-zone
- perform evidence ingestion, normalization, and preservation on Linux
- define all invariants, schemas, and guarantees under Linux semantics

AEGIS MAY:

- ingest artifacts originating from Windows systems
- accept Windows-derived files, logs, and metadata
- observe Windows environments via exported or collected evidence
- normalize Windows-origin data within the Linux-based Observation Plane

Windows-derived data is treated as **input**, not **authority**.

---

## Rationale

This design veto is grounded in the following principles:

1. **Evidence Integrity**  
   Governance systems must observe from a position of determinism. Linux provides stronger guarantees for low-level inspection, permission modeling, and auditability.

2. **Isolation by Design**  
   AEGIS must remain operationally independent from the environments it observes. Hosting on Windows collapses the observer/observed boundary.

3. **Authority Preservation**  
   Allowing Windows to host AEGIS would implicitly grant it authority over system invariants. This is unacceptable.

4. **Scope Discipline**  
   Supporting Windows as a host platform expands surface area without proportional governance benefit and increases failure modes.

---

## Explicit Non-Claims

This veto does **not** assert that:
- Windows systems are insecure or invalid
- Windows environments lack operational importance
- Windows-derived data is untrustworthy by default
- AEGIS will not analyze or reason about Windows systems

This veto applies strictly to **where AEGIS lives**, not **what AEGIS can see**.

---

## Conditions for Reconsideration

This design veto SHALL remain in effect unless compelling, concrete evidence demonstrates that:

- Windows hosting can meet or exceed Linux determinism guarantees
- shadow-zone isolation can be preserved
- evidence integrity is not degraded
- overall system complexity is reduced rather than increased

Absent such evidence, this veto stands indefinitely.

---

## Closing Declaration

AEGIS does not ignore Windows.

AEGIS refuses to be governed by it.

This veto preserves architectural integrity, authority boundaries, and long-term trustworthiness.

---
