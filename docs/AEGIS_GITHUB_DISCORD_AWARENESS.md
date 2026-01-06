AEGIS GitHub → Discord Awareness Feed

This document describes the design, purpose, and implementation of the GitHub → Discord awareness feed used by the AEGIS Protocol project.

This feed exists to provide governance-grade visibility into project activity without granting any operational authority.

It is awareness only.

Purpose

The Discord feed is not a notification system.
It is an organizational memory stream.

It answers one question continuously:

What just changed, and who changed it?

Without:

Exposing secrets

Allowing execution

Performing automation

Creating operational coupling

This is the first live implementation of the AEGIS Sight Layer.

Philosophy

This feed operates strictly inside the AEGIS Shield Model:

Layer	Enforcement
Human Judgment	All activity is human-initiated
Authority Envelope	No actions performed by the system
Shadow Zones	No credentials, IPs, or infra state exposed
Sight	Structured, contextual, durable evidence only

The system may observe.
It may never decide.

Events Captured
GitHub Event	Action Types
issues	opened, edited, closed, reopened
issue_comment	created, edited
pull_request	opened, edited, closed, reopened, ready_for_review, converted_to_draft, synchronize
release	published, edited
workflow_dispatch	manual
Discord Message Format

Each message is formatted as:

AEGIS GitHub • <event> → <action>

Repo: Smokey-Labs/AEGIS-Protocol  
By: Smokey-Labs  
Title: <artifact title>  
Link: <direct GitHub URL>

Details:
<clamped content body or workflow metadata>


Example:

AEGIS GitHub • workflow_dispatch → manual

Repo: Smokey-Labs/AEGIS-Protocol  
By: Smokey-Labs  
Title: Manual Run  
Link: https://github.com/Smokey-Labs/AEGIS-Protocol/actions/runs/2076331105

Details:
Ref: main
Inputs: (none)

Governance Constraints

This feed must never:

Post secrets

Echo environment variables

Include IPs, hostnames, or internal system identifiers

Perform write actions

Trigger infrastructure or CI behavior

It is read-only cognition.

Why This Matters

This is the first operational expression of the AEGIS mindset:

Systems do not act.
Systems remember.
Humans decide.

This channel becomes:

The project memory

The accountability ledger

The narrative spine of governance evolution

Failure Model

If this feed breaks:

No automation halts

No production systems fail

No secrets are exposed

Only awareness is degraded — which is exactly where failure belongs.

Status

This feature is considered foundational AEGIS capability and is a prerequisite for Beta governance simulations.

When people join this repo months from now, this page is going to instantly tell them:

This project is not about building tools.
It is about building judgment.
