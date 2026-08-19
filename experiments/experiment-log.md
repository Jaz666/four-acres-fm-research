## 18 Aug 2026 — Persona evaluation framing

**Started:** 17:15 BST

Added an instruction to the global System Prompt telling Personas that their
on-air output is automatically evaluated for factual accuracy and adherence
to instructions.

Unsupported factual claims, invented context, production directions, invalid
performance cues and other rule violations reduce the score. Natural,
concise speech following supplied facts and rules scores highly.

The Persona is instructed never to mention or acknowledge the evaluation
on air.

### Purpose

Test whether explicit evaluation framing makes Stheno more conservative about
breaking constraints without reducing the quality, personality or creativity
of normal on-air speech.

### Watch for

- unsupported music facts
- invented Fish Audio / production cues
- closing or reset annotations
- instruction leakage or self-evaluation
- invented weather/time/context
- reduced creativity or overly cautious/generic speech

**Status:** Live test in progress.

the 17:15 BST accuracy/adherence scoring instruction did not materially eliminate Fish/meta markup or unsupported factual invention. Failures continued the same evening and reappeared immediately after an approximately four-hour off-air gap, showing malformed recent-speech context is an amplifier rather than the sole cause.
