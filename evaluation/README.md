# Evaluation Framework

Phase 0 establishes the benchmark contract before we select production speech/translation providers.

## Initial evaluation dimensions

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

The benchmark should eventually contain consented or synthetic, human-verified examples covering:

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

## Golden rule

Fluency is not correctness. A fluent translation that changes a medication dose, negation, allergy, or other clinically important fact is a critical failure.

## Data handling

Do not commit real patient data to this repository. Local benchmark data belongs under ignored paths and must follow the project's future consent and governance requirements.
