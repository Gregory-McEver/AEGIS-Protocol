# Signal Forge — Signal Taxonomy v1

## Purpose

This document defines the **v1 Signal Taxonomy** for **Signal Forge**, the Layer 2 component of AEGIS.

Signal Forge transforms deterministic observations (`EVT:*`) from the Observation Plane into **bounded governance signals**.

Signals are:
- structured
- deterministic
- evidence-referenced
- non-narrative
- non-accusatory

Signals are **not alerts** and **not decisions**.  
They indicate that governance-relevant conditions exist and warrant human awareness or further interpretation.

---

## Signal Forge Scope

Signal Forge:
- correlates normalized events over time windows
- evaluates invariants, baselines, and attribution completeness
- emits signals when defined conditions are met

Signal Forge does **not**:
- infer intent
- assign blame
- enforce policy
- initiate remediation
- generate narrative explanation

Interpretation of signals is explicitly delegated to **Aurora Analytics** or humans.

---

## EVT — Normalized Event

`EVT:*` references represent normalized, deterministic observations captured by the Observation Plane.

EVTs:
- describe that something occurred
- are timestamped
- are scoped to one or more entities (host, user, service)
- may reference evidence artifacts

EVTs do **not**:
- assert correctness
- assert compliance
- assert intent
- contain narrative explanation

Signals are derived exclusively from EVT sequences and evidence references.

---

## Signal Structure (Conceptual)

Each signal emitted by Signal Forge includes:

- `signal_type`
- `time_window`
- `entities` (host/user/service)
- `risk_weight` (LOW | MED | HIGH)
- `confidence` (LOW | MED | HIGH)
- `evidence_refs[]`
- optional `invariant_refs[]`

---

## Signal Definitions (v1)

### 1. ANOMALY

**Definition:**  
Observed behavior deviates from established baseline patterns for the given entity or system.

**Claims**
- Observed behavior is unusual relative to historical norms.

**Non-claims**
- Does not claim fault, risk, or policy violation.
- Does not claim intent.

**Required evidence**
- `EVT:*` references demonstrating deviation from baseline.

**Typical triggers**
- Sudden increase in privileged commands.
- Service restarts outside normal windows.

**Default risk guidance**
- LOW → MED depending on scope and privilege.

---

### 2. ATTRIBUTION_GAP

**Definition:**  
A governance-relevant action occurred without sufficient context to associate it with an approved or declared process artifact.

**Claims**
- Action occurred.
- Attribution context is missing or incomplete.

**Non-claims**
- Does not claim maliciousness.
- Does not claim policy violation unless paired with another signal.

**Required evidence**
- `EVT:*` establishing the action.
- Evidence showing missing context linkage.

**Typical triggers**
- Config change with no associated change context.
- Privileged command execution outside declared window.

**Default risk guidance**
- MED → HIGH depending on privilege and reversibility.

---

### 3. EVIDENCE_GAP

**Definition:**  
A signal condition was detected, but required supporting evidence could not be resolved or validated.

**Claims**
- Evidence expected but unavailable.

**Non-claims**
- Does not invalidate the observed event.
- Does not imply concealment.

**Required evidence**
- Reference to missing or unresolved evidence artifact.

**Typical triggers**
- Log rotation removed required offset.
- Evidence artifact inaccessible.

**Default risk guidance**
- MED when repeated or paired with other signals.

---

### 4. INVARIANT_BREACH

**Definition:**  
A declared invariant was crossed based on available deterministic evidence.

**Claims**
- Invariant condition was violated.

**Non-claims**
- Does not claim malicious intent.
- Does not prescribe response.

**Required evidence**
- `EVT:*` proving condition occurred.
- `INVARIANT:*` reference.

**Typical triggers**
- Privileged identity created without required context.
- Backup disabled on Tier-1 system.

**Default risk guidance**
- HIGH.

---

### 5. PRESSURE_PATTERN

**Definition:**  
Repeated exceptions or overrides indicate sustained operational pressure affecting governance posture.

**Claims**
- Repetition suggests normalization of exception behavior.

**Non-claims**
- Does not assign blame.
- Does not imply negligence.

**Required evidence**
- Multiple `EVT:*` across defined window.

**Typical triggers**
- Frequent break-glass usage.
- Repeated emergency changes.

**Default risk guidance**
- MED → HIGH when persistent.

---

### 6. INTEGRITY_THINNING

**Definition:**  
Longitudinal patterns indicate gradual erosion of governance discipline.

**Claims**
- Governance safeguards are weakening over time.

**Non-claims**
- Does not assert wrongdoing.
- Does not assert imminent failure.

**Required evidence**
- Historical EVT patterns.
- Prior signals supporting trend.

**Typical triggers**
- Declining peer review frequency.
- Reduced documentation over time.

**Default risk guidance**
- MED.

---

### 7. CONFIG_DRIFT

**Definition:**  
Configuration state diverges from declared or expected baseline.

**Claims**
- Drift exists relative to baseline.

**Non-claims**
- Does not claim incorrectness.
- Does not claim risk severity.

**Required evidence**
- Config diff evidence.
- EVT referencing change.

**Typical triggers**
- Repeated systemd unit edits.
- Untracked config modifications.

**Default risk guidance**
- MED.

---

### 8. SERVICE_HEALTH_DEGRADATION

**Definition:**  
Service health indicators show sustained degradation beyond transient fluctuation.

**Claims**
- Reliability trend is declining.

**Non-claims**
- Does not assert root cause.

**Required evidence**
- Health EVT sequences.
- Service state evidence.

**Typical triggers**
- Repeated restarts.
- Increasing error rates.

**Default risk guidance**
- MED → HIGH depending on tier.

---

### 9. BACKUP_ROT

**Definition:**  
Backup mechanisms are failing or producing unreliable recovery artifacts.

**Claims**
- Backup integrity is compromised.

**Non-claims**
- Does not assert data loss has occurred.

**Required evidence**
- Backup job EVT failures.
- Verification failure evidence.

**Typical triggers**
- Repeated backup failures.
- Verification mismatches.

**Default risk guidance**
- HIGH.

---

### 10. CAPACITY_RISK

**Definition:**  
System capacity trends indicate impending constraint or exhaustion.

**Claims**
- Capacity pressure is increasing.

**Non-claims**
- Does not assert immediate failure.

**Required evidence**
- Capacity EVT metrics over time.

**Typical triggers**
- Disk nearing exhaustion.
- Memory pressure trends.

**Default risk guidance**
- MED → HIGH.

---

### 11. PRESERVATION_TRIGGERED

**Definition:**  
Preservation actions were automatically initiated due to detected risk of irreversible change.

**Claims**
- Preservation threshold was crossed.
- Evidence snapshot was taken.

**Non-claims**
- Does not assert incident severity.

**Required evidence**
- Preservation action EVT.
- Triggering signal references.

**Default risk guidance**
- HIGH.

---

### 12. PRESERVATION_RECOMMENDED

**Definition:**  
Conditions suggest preservation should occur before further action.

**Claims**
- Risk of evidence loss exists.

**Non-claims**
- Does not mandate preservation.

**Required evidence**
- EVT patterns indicating risk.

**Typical triggers**
- Rapid privileged changes.
- Incident response conditions.

**Default risk guidance**
- MED.

---

## Closing Notes

- Signals are **inputs to governance**, not outputs of enforcement.
- Signal Forge must always prefer **UNKNOWN** over speculation.
- Narrative interpretation is explicitly delegated to Aurora Analytics.

This taxonomy defines what Signal Forge may emit — nothing more.

---

## Appendix A — Temporal Integrity & Truth Survivability

This appendix defines how Signal Forge handles time, delay, and irreversible change to ensure that truth is not lost due to timing artifacts.

Signal Forge prioritizes **truth survivability over timeliness**.

---

### A.1 Time Domains

Signal Forge operates across four distinct time domains:

#### Event Time
The timestamp at which the observed action or condition occurred in the source system.

- Recorded within `EVT:*`
- May arrive late or out of order
- Represents when reality happened

#### Ingestion Time
The timestamp at which the Observation Plane recorded the event.

- Always greater than or equal to Event Time
- Represents when AEGIS became aware

#### Correlation Window
The analytic time window used to evaluate patterns and thresholds.

- Sliding windows (e.g., 5m, 1h, 24h)
- Used for pattern detection only
- **Not** a gate for truth validity

#### Preservation Horizon
The time span during which preservation of evidence remains relevant.

- Always longer than correlation windows
- Anchored to irreversible change, not signal emission
- Defines how far back context must be considered before destructive actions

---

### A.2 Principle: No Single Time Window May Gate Truth

Signal Forge enforces the following invariant:

> **No irreversible system change may rely on a single temporal window to preserve truth.**

Operational implications:
- Signals may be emitted retroactively
- Late-arriving evidence remains valid
- Missed detection does not imply absence of risk
- Preservation decisions must consider historical context beyond immediate windows

---

### A.3 Late-Arriving Events

Signal Forge explicitly supports **retrospective signaling**.

If an `EVT:*` arrives after the analytic window in which it would normally be evaluated:

- The event is still processed based on its Event Time
- Signals may be emitted with historical context
- Signal timestamps reflect the original time window, not ingestion time

Example:
- Storage degradation occurred prior to remediation
- Evidence arrives after remediation
- Signal Forge emits `SERVICE_HEALTH_DEGRADATION (historical)`

This behavior is intentional and correct.

Truth delayed is acceptable.  
Truth lost is not.

---

### A.4 Preservation Horizon Semantics

Preservation decisions must not depend solely on active signals.

Before any **irreversible administrative action**, Signal Forge (or a preservation guard) must evaluate:

- Recent `EVT:*` indicators within the preservation horizon
- Prior signals related to the affected system or entity
- Evidence gaps or attribution gaps within the horizon

If risk indicators exist within the horizon:
- `PRESERVATION_RECOMMENDED` may be emitted
- `PRESERVATION_TRIGGERED` may be executed if configured

Preservation may occur:
- before signal emission
- after signal emission
- or retroactively based on late-arriving evidence

Preservation captures **context**, not causality.

---

### A.5 Missed Preservation as Evidence

If an irreversible action occurs and preservation was not performed despite the presence of risk indicators:

This condition must not be silent.

Signal Forge may emit:
- `ATTRIBUTION_GAP`
- `EVIDENCE_GAP`
- or `INVARIANT_BREACH` (if preservation was required by policy)

This records that:
- a preservation opportunity existed
- evidence context was reduced or lost

This is not a judgement of intent or fault.

It is a record of lost observability.

---

### A.6 Aurora Analytics and Time

Aurora Analytics consumes Signal Forge outputs with full awareness of temporal context.

Aurora must:
- distinguish Event Time from Ingestion Time
- acknowledge late-arriving evidence
- explicitly state when conclusions are retrospective
- prefer UNKNOWN over speculative reconstruction

Aurora does not assume real-time omniscience.

Aurora communicates **temporal truth**, not immediacy.

---

### A.7 Failure Posture

When time-related ambiguity exists, Signal Forge must fail safely:

- Emit fewer signals rather than speculative ones
- Preserve evidence where possible
- Record uncertainty explicitly
- Avoid narrative reconstruction

This ensures that timing artifacts degrade confidence, not integrity.

---

### A.8 Summary Invariant

Signal Forge is designed so that:

- Time may delay awareness
- Time may complicate interpretation
- Time may reduce available evidence

But **time must never erase the existence of truth**.

---


