# Phase 1 Benchmark Cases

Phase 1 evaluates speech and translation providers before selecting production components.

## Required categories

- Ordinary Bangla (`bn-BD`)
- Bangla-English code switching
- Medical symptoms
- Medication names
- Dosages and units
- Numbers and measurements
- Negation
- Dates and durations
- Uncertainty/hedging
- Rapid speech
- Background noise
- Elderly speakers
- Regional/accent variation

## Critical-error policy

A benchmark case is a critical error when a system changes or drops information that could materially alter clinical meaning, especially medication, dose, number, unit, allergy, negation, duration, or uncertainty.

Critical errors should be reported separately from aggregate WER/BLEU-style metrics. A low average error rate is not sufficient if critical information is being corrupted.

## Data governance

Only use synthetic, public-domain, explicitly licensed, or appropriately consented recordings. Do not commit raw patient audio, identifiable transcripts, credentials, API keys, or other sensitive data to Git.

## Provider comparison

For each provider/configuration record:

- model/provider and version
- language/locale
- audio conditions
- transcription output
- reference transcription
- medical-term accuracy
- number/dose accuracy
- medication-name accuracy
- negation accuracy
- semantic translation accuracy
- latency (first partial, final transcript, final translation, TTS start)
- failure/timeout rate
- estimated cost per minute

Do not select a provider from a single demo. Selection requires repeatable benchmark evidence.
