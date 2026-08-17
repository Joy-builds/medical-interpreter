# Medical Interpreter

AI-assisted real-time medical interpretation for Bangla (bn-BD) ↔ English conversations.

> **AI handles the volume. Professionals handle the exceptions. Patients get heard.**

## Project status

**Phase 0 — Foundation**

This repository is intentionally starting small. The first goal is to establish stable architecture, safety boundaries, evaluation contracts, and replaceable interfaces before connecting speech or translation providers.

## Product boundary

This system is a **medical interpretation tool**, not an AI doctor.

It may:
- transcribe speech;
- translate faithfully between Bangla and English;
- preserve clinically important details;
- detect uncertainty or potential interpretation errors;
- request clarification;
- escalate a session to a professional interpreter.

It must not:
- diagnose patients;
- prescribe or change treatment;
- invent missing information;
- silently alter medication names, doses, numbers, units, allergies, symptoms, negation, dates, duration, or uncertainty.

## Target workflow

1. A healthcare organization starts a session from a browser.
2. A patient speaks Bangla into a clinic device.
3. Bangla speech is transcribed and translated into medical English for the doctor.
4. The doctor responds in English.
5. The response is transcribed, translated into Bangla, and spoken to the patient.
6. A professional Bengali interpreter can monitor multiple sessions and take over whenever the system flags uncertainty or risk.

Patients should not need individual accounts for the initial workflow.

## Long-term platform

The architecture is intended to become a multi-tenant SaaS platform for interpreter agencies, hospitals, clinics, telemedicine providers, NGOs, and other healthcare organizations. Each tenant must have isolated users, sessions, permissions, configuration, and data.

## Development phases

- **Phase 0:** foundation, architecture, contracts, safety boundaries, evaluation framework
- **Phase 1:** ASR/TTS/translation benchmarking and a single realtime conversation
- **Phase 2:** medical validation, uncertainty detection, confirmation, escalation, audit logging
- **Phase 3:** supervisor dashboard and human takeover/return-to-AI
- **Phase 4:** multi-tenant SaaS and organization workflows
- **Phase 5:** scalable production infrastructure, security, privacy, billing, analytics, integrations
- **Phase 6:** real-world validation, optimization, and model specialization based on verified data

The exact implementation order may change as evidence from benchmarking and clinical testing comes in. The product boundary and safety principles do not.

## Repository layout

```text
apps/          browser applications
services/      backend/realtime services
packages/      shared contracts and utilities
evaluation/    benchmark datasets, runners, and metrics
docs/          architecture, safety, privacy, and product decisions
```

## Safety principle

When the system is uncertain about clinically important content, **do not guess**. Preserve the original statement, surface the uncertainty, and escalate or request clarification.
