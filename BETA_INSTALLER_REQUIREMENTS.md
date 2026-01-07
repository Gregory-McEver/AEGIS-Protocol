# Beta Installer Requirements

This document defines the mandatory behavior for the two AEGIS installer roles.

---

## AEGIS CORE Install

**Package:** `aegis-core_<version>.deb`  
**Role:** Central authority, governance engine, and decision boundary.

### Responsibilities
- Host compiled governance snapshot
- Maintain system ledger / database
- Run validation and drift detection engines
- Expose API / bridge for PAGE nodes
- Execute foresight and hindsight workflows

### Must Install
- `/opt/aegis/core/`
- `/etc/aegis/`
- `/var/lib/aegis/`
- systemd units:
  - `aegis-core.service`
  - `aegis-foresight.timer`
  - `aegis-hindsight.timer`

### Must Never
- Perform destructive system actions by default
- Accept unverified PAGE nodes
- Load unsigned governance snapshots

---

## AEGIS PAGE Install

**Package:** `aegis-page_<version>.deb`  
**Role:** Distributed observation and evidence forwarding.

### Responsibilities
- Execute collectors and probes
- Spool evidence locally if CORE is unavailable
- Forward evidence securely to CORE
- Operate under strict read-only authority

### Must Install
- `/opt/aegis/page/`
- `/etc/aegis/page.conf`
- `/var/lib/aegis/spool/`
- systemd units:
  - `aegis-page.service`
  - `aegis-page.timer`

### Must Never
- Take action beyond evidence collection
- Modify host state
- Bypass CORE validation

---

## Enforcement Rule

A PAGE node cannot operate without an authenticated CORE.  
A CORE must reject any PAGE not bound to a declared Authority Envelope.
