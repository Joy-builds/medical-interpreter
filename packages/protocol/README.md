# Realtime Protocol Foundation

This package will define provider-neutral contracts shared by the browser, realtime gateway, AI services, and supervisor system.

Phase 0 deliberately defines the event vocabulary before implementing a provider.

## Session

A session represents one patient-doctor interpretation conversation.

Required conceptual fields:

- `session_id`
- `tenant_id`
- `language_pair` (`bn-BD` ↔ English initially)
- `status`
- `created_at`
- `supervisor_id` (optional)

## Event types

The eventual realtime protocol should support at least:

- `session.created`
- `session.started`
- `audio.started`
- `audio.stopped`
- `transcript.partial`
- `transcript.final`
- `translation.ready`
- `validation.passed`
- `validation.warning`
- `human.escalation_requested`
- `human.takeover_started`
- `human.takeover_ended`
- `session.ended`
- `error`

The exact wire format belongs to the implementation phase, but the semantic events should remain stable so providers can be swapped without rewriting the application.

## Design rule

A transcript, translation, validation result, and audio output are separate events. This allows the UI and supervisor system to see what the system heard, what it translated, and whether the translation passed critical-information checks.
