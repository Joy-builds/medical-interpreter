# Evaluation Framework

Phase 1 is evidence-first. The purpose is to determine which speech, translation, and TTS components can support the medical-interpreter pipeline.

## Workflow

1. Prepare approved synthetic/public/consented benchmark cases.
2. Run the same cases through every candidate provider/configuration.
3. Score transcription and translation quality.
4. Separately score critical information preservation.
5. Measure realtime latency and reliability.
6. Record cost and data-handling characteristics.
7. Select the initial provider combination from the results.

## Evaluation dimensions

### Speech recognition

- Bangla `bn-BD` word error rate (WER)
- English WER
- medical-term accuracy
- medication-name accuracy
- number accuracy
- dose/frequency accuracy
- negation accuracy
- performance under noise
- accent/dialect robustness

### Translation

- semantic fidelity
- medical terminology fidelity
- number/dose preservation
- unit preservation
- negation preservation
- date/duration preservation
- uncertainty preservation
- ambiguity handling
- critical-error rate

### Realtime experience

- time to first partial transcript
- end-of-turn latency
- translation latency
- time to first synthesized audio
- interruption/recovery behavior

### Cost and operations

- cost per interpreted minute
- concurrent-session capacity
- error/retry rate
- provider rate limits

## Dataset categories

The benchmark should contain consented or synthetic, human-verified examples covering:

- everyday Bangla medical speech;
- Bangla-English code switching;
- regional pronunciation variation;
- elderly speakers;
- clinic/background noise;
- medication names and brand/generic names;
- numbers, doses, units, and frequencies;
- symptoms and body locations;
- explicit negation;
- uncertainty;
- dates and durations;
- fast and interrupted speech.

See `benchmark.schema.json`, `benchmark.example.json`, `benchmark-cases.md`, and `provider-matrix.md`.

## Golden rule

Fluency is not correctness. A fluent translation that changes a medication dose, negation, allergy, or other clinically important fact is a critical failure.

## Data handling

Do not commit real patient data to this repository. Raw audio and identifiable transcripts must stay in approved storage outside Git, with appropriate consent and access controls.
