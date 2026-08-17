# Services

Phase 1 service boundaries will live here. Keep provider integrations behind stable interfaces so ASR, translation, and TTS providers can be benchmarked and replaced independently.

Planned boundaries:

- `speech`: realtime audio input/output and ASR adapters
- `translation`: medical-aware translation adapters
- `tts`: text-to-speech adapters
- `realtime`: session orchestration and turn handling

No provider is selected as production-default until benchmark evidence supports it.
