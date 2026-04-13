# Machine Learning Paper Guidelines

Use this reference when the source paper is in machine learning, deep learning, or adjacent AI methods.

## Core Principle

Do not accidentally turn the talk into a full ML tutorial unless the user explicitly wants that.

Background should exist only to support understanding of the paper's contribution.

## Audience Calibration

### Audience: No ML Background

Prioritize:

- Task definition
- Why the old approach feels limited
- Intuition for the new method
- What the experiments prove

Reduce:

- Dense notation
- Training details
- Long derivations

### Audience: Some ML Background

Prioritize:

- Method pipeline
- Key module logic
- The most important formulas
- Why the design differs from prior approaches

### Audience: Strong Technical Background

Prioritize:

- Architectural tradeoffs
- Precise module behavior
- Experimental setup and ablations
- Limits and assumptions

## Formula Policy

Ask explicitly how much formula content should remain.

Useful levels:

- `Low`: almost no formulas, mostly intuition
- `Medium`: keep only core formulas with plain-language explanation
- `High`: allow several formulas when they are central to understanding

Never keep formulas just because they are in the paper.

## Background Depth Control

For old methods:

- Explain the mechanism only until the audience can understand the new method's design motive
- Stop before the background becomes its own curriculum

Good stopping rule:

- If removing one old-method detail would not hurt understanding of the new method, cut it

## Experiment Slides

Results slides should answer:

- What claim is being tested
- What evidence supports that claim
- Why the result matters

Do not present experiments as a scoreboard with no interpretation.

## Example: Attention Is All You Need

For cross-domain audiences with little ML background:

- `problem-driven` usually works best
- `technical-evolution` can also work if old methods are compressed aggressively

For method-focused teaching:

- `technical-evolution` is often stronger because it reveals why Transformer replaced earlier pipelines