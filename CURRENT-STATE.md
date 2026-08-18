# Current Four Acres FM Experimental State

Last updated: 18 August 2026

## Models

- Persona: Stheno 8B Q5_K_S
- Producer/editorial selection: Qwen3-4B, CPU
- Discovery router: fine-tuned FunctionGemma 270M, CPU
- TTS: local Fish Audio

## Current live experiment

FunctionGemma performs initial track-discovery routing.
Qwen receives the grounded candidate set and makes the final
editorial track selection.

Early live testing suggests introducing FunctionGemma has reduced
track-selection latency by approximately 5 seconds.

## Current Persona experiment

Revised global System Prompt / House Rules introduced approximately
09:42 BST, 18 August.

Primary targets:
- unsupported factual invention
- invented environmental context
- backstage/meta output leakage
- invalid Fish Audio bracket tags

## Currently watching

- FunctionGemma routing failures
- Qwen fallback frequency
- Persona factual invention
- Fish Audio closing/reset tags
- Sponsor Spot absurdity
