# Route Patterns

## Problem-Driven

Use when:

- The audience is not deeply familiar with the technical stack
- The talk must justify why the paper matters
- The user wants a clear chain of `problem -> limitation -> method -> evidence`

Strengths:

- Best for zero- or low-background audiences
- Keeps attention on motivation and value
- Prevents long background detours

Risks:

- Technical evolution may feel compressed
- Old methods may seem underexplained

Typical slide chain:

1. What task or problem the paper addresses
2. Why prior approaches are insufficient
3. The key idea behind the new method
4. The main components of the method
5. Experiments that prove the idea
6. Final impact or takeaway

## Technical-Evolution

Use when:

- The audience must understand how the new method replaces or upgrades prior methods
- The paper sits in a visible historical transition
- The user explicitly wants to compare old and new pipelines through explanation, not a comparison table

Strengths:

- Excellent for explaining design motivation
- Makes mechanism differences easy to teach
- Strong fit for "why did this method emerge" talks

Risks:

- Background can become too long
- The main method may arrive too late if old methods are overexplained

Typical slide chain:

1. What kind of task is being solved
2. How the old method works
3. What bottlenecks the old method has
4. What transitional idea appears
5. How the new method changes the core pipeline
6. Why the new structure solves the earlier bottlenecks
7. Evidence and impact

## Result-Driven

Use when:

- Time is very short
- The audience mainly cares about gains, conclusions, or takeaways
- The talk is closer to defense, interview, or executive summary than teaching

Strengths:

- Fast and focused
- Good for short presentations
- Keeps the contribution visible from the start

Risks:

- Can weaken intuition for the method
- May feel shallow for learning-oriented audiences

Typical slide chain:

1. Core claim of the paper
2. Why that claim matters
3. Minimal method overview
4. Key evidence
5. Limits, value, and takeaway

## Selection Heuristics

- Choose `problem-driven` if the user emphasizes understanding, accessibility, or mixed-background listeners
- Choose `technical-evolution` if the user emphasizes differences between old and new methods
- Choose `result-driven` if slide count is tight and the audience mainly wants conclusions

If torn between `problem-driven` and `technical-evolution`:

- Prefer `problem-driven` for non-technical or cross-domain audiences
- Prefer `technical-evolution` for method-focused teaching