# ADR 001: Provider-Neutral AI Pipeline

**Status:** Accepted for Phase 0

## Decision

Keep speech recognition, translation, validation, and text-to-speech behind provider-neutral service interfaces.

## Context

The initial product depends on accurate Bangla (`bn-BD`) speech handling. Provider quality, latency, pricing, and language support must be benchmarked rather than assumed. A single-vendor architecture would make experimentation and replacement unnecessarily expensive.

## Consequences

Positive:
- ASR/TTS/translation providers can be benchmarked independently.
- A poor provider can be replaced without redesigning the product.
- Evaluation can compare providers using the same session protocol.

Tradeoff:
- We must maintain internal interfaces and adapters.
- Some provider-specific capabilities may need optional extensions.

## Non-goal

This ADR does not select a production vendor. Vendor selection belongs to Phase 1 after benchmark evidence exists.
