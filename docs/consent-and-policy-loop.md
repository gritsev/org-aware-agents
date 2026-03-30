# Consent and policy loop

## The problem

When multiple agents operate inside one organization, sooner or later they hit questions that are not purely operational:
- is this action allowed
- should we change the threshold
- who needs to approve
- should a risky exception be accepted
- does the policy still reflect reality

If the answer lives only in chat, the system becomes ungovernable.

## The pattern

Use an explicit consent and policy loop.

At a high level:
1. an agent encounters a boundary or disagreement
2. instead of improvising, it starts a structured consent / approval process
3. the process produces one of:
   - approval for a concrete action
   - rejection
   - clarification request
   - a policy update proposal
4. the result is written back into the operating system, not left in conversation history

## Why this matters

This gives you:
- safer autonomy
- repeatable decisions
- lower manager bottlenecks
- better auditability
- a path for policy improvement over time

## Human and agent coordination

The same loop can serve both:
- human-only decisions
- human-agent approvals
- agent-agent disagreements that require human escalation

## Practical principle

High-risk ambiguity should create a governance event, not a clever guess.

