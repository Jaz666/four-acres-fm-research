Skill prompt tracing shows global Fish/output guidance appears well after the skill task, context and recent-speech examples. Recent speech can itself contain Fish cues and malformed annotations, creating accidental few-shot reinforcement. Proposed mitigation: local output-safety reminder near generation + sanitised recent-speech context + proxy boundary validation.

as a Skill V2 architectural decision: move output safety from prompt-only control to deterministic post-generation normalisation, and sanitise recent-speech memory before reuse.

## Skill prompt leakage / self-evaluation — 18 Aug 2026

### Observation

Legacy skills appear substantially more prone to Persona output leakage than
ordinary links.

A particularly severe `sponsor-spotv2` example under Stheno produced the
bumper, then continued by evaluating its own compliance with the skill brief:

> Note:
> - The company name (...) is completely new and fits the Lancashire business style.
> - The second sentence states a factual, ordinary claim about the product (...),
>   without trying to be humorous or write marketing copy.

The response also invented its own Fish Audio cue:

> [calm and conversational tone]

### Interpretation

This is stronger evidence than the earlier `[End of ...]` failures.

The Persona is not merely adding unwanted markup. It can cross the boundary
between performing the skill and discussing/evaluating the instructions used
to generate it.

Prompt tracing showed that legacy skill calls expose the Persona to a detailed
skill brief, context and recent speech before the global System Prompt /
House Rules containing output-safety guidance.

Recent speech may also contain malformed previous outputs, creating accidental
few-shot reinforcement.

### Decision

Do not continue escalating legacy skill prompts with additional prohibitions.

Address this structurally in Skill V2.

Proposed principles:

1. Separate skill reasoning/specification from the final Persona performance
   contract where possible.
2. Put a small, hard output contract immediately adjacent to Persona generation.
3. Deterministically normalise Persona output before it reaches TTS.
4. Store/replay sanitised spoken text in recent-speech context rather than raw
   model output containing performance/meta markup.
5. Treat prompts as creative steering; enforce the broadcast boundary in code.
6. Add regression tests for:
   - `[End of ...]`
   - `(Sponsor end)`
   - reset cues such as `[back to regular speaking voice]`
   - `Note:` / bullet-point self-evaluation
   - task/instruction explanations
   - invented second performance cues

### Current status

Legacy Sponsor Spot V1 and V2 disabled on 18 Aug 2026 following repeated
malformed output.

Sponsor Spot V3 remains the current experimental version.
