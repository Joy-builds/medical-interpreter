# Multi-Tenancy and Security Foundation

## Tenant model

The platform is a shared SaaS deployment serving many organizations. Every customer organization is a tenant.

All tenant-owned resources must carry an explicit tenant scope, including:

- users and roles;
- sessions;
- participants;
- transcripts;
- alerts;
- audit events;
- configuration;
- usage and billing records.

Cross-tenant access is forbidden by default.

## Authorization

Authentication answers **who** the user is. Authorization answers **which tenant resources** that user may access. Both are required for every protected operation.

Recommended roles for the eventual platform:

- `org_admin` — organization configuration and users;
- `supervisor` — active sessions, alerts, human takeover;
- `operator` — permitted session operations;
- `viewer` — limited read-only access.

The exact role set can evolve, but least privilege is mandatory.

## Session isolation

A realtime session must have an unguessable identifier and an authenticated tenant context. Audio, transcript events, and control events must never be routable across tenant boundaries.

## Sensitive data

Treat medical audio, transcripts, and derived clinical information as sensitive. Production storage and retention requirements must be defined before real patient data is used.

Do not place secrets, API keys, tokens, or patient data in source control.

## Auditability

Security-sensitive events should eventually be auditable, including:

- session creation and termination;
- transcript/translation corrections;
- supervisor access;
- human takeover and return-to-AI;
- permission changes;
- data export/deletion actions.

## Initial rule

Phase 0 uses synthetic/local evaluation data only. No real patient information should be committed to this repository or used in development without an approved data-governance process.
