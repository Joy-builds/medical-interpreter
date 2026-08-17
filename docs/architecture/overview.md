# Architecture Overview

## Core principle

The system is a collection of replaceable realtime services rather than one provider-specific AI box.

```text
Patient/Doctor browser
        │
        │ realtime audio
        ▼
Realtime session gateway
        │
        ├── speech recognition
        ├── medical translation
        ├── critical-detail validation
        ├── uncertainty/risk detection
        └── speech synthesis
        │
        ▼
Translated text + audio
        │
        ▼
Other participant

Supervisor control plane
        │
        ├── active sessions
        ├── alerts
        ├── transcript review
        ├── human takeover
        └── return-to-AI
```

## Separation of concerns

### Realtime transport
Responsible for low-latency audio transport, turn detection, session lifecycle, reconnects, and participant state. It must not contain provider-specific medical translation logic.

### Speech recognition
Converts audio into timestamped transcripts. Provider/model selection is an implementation detail behind a stable interface. `bn-BD` is the initial Bangla target.

### Medical translation
Produces a faithful translation while preserving clinically important meaning. Translation is not diagnosis or treatment advice.

### Validation
Checks critical information independently from the translation generation step. At minimum, the design must account for medications, dosage, numbers, units, allergies, symptoms, negation, dates/durations, uncertainty, and ambiguity.

### Speech synthesis
Turns an accepted translation into speech. TTS providers must be replaceable and evaluated for Bangla intelligibility and medical-term pronunciation.

### Human escalation
A session can transition from AI handling to human takeover without losing conversational state. Human control can later be returned to AI.

## Scaling model

A single deployment should support many isolated sessions concurrently. A session is a logical unit of state; workers should be horizontally scalable rather than permanently bound to one customer or patient.

```text
                 Load balancer
                      │
          ┌───────────┼───────────┐
          ▼           ▼           ▼
       worker      worker      worker
          │           │           │
          └───────────┼───────────┘
                      ▼
                session store
                      │
                 tenant data
```

The platform is multi-tenant from the beginning. Every request that touches customer data must be scoped to an authenticated tenant and authorized user.

## Initial client workflow

- Organization user authenticates.
- Organization creates an interpretation session.
- Patient uses a clinic-provided browser/device; no patient account is required for the initial workflow.
- Patient and doctor take turns speaking.
- The system displays transcripts and plays translations.
- Supervisor receives alerts and can take over.

## Provider strategy

ASR, translation, and TTS must be benchmarked independently. Do not hard-code the product around a single vendor before Phase 1 evaluation.
