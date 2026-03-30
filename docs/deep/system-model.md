# System model

This document is the detailed public version of the core thesis in `../quick/responsibility-model.md`.

The main design move is simple:
- humans and agents should operate inside the same organizational language
- the language should be explicit enough to drive system behavior
- delegation should preserve responsibility boundaries instead of bypassing them

## 1. Organization as executable context

The organization is modeled as a hierarchy of responsibility domains.

Each domain should define:
- purpose
- authority boundaries
- internal and external customers
- suppliers and dependencies
- expected outcomes
- metrics and constraints

In Sociocracy-style language, a domain is the area of responsibility.

That matters because domain context is richer than:
- "you are a helpful assistant"
- "your role is sales"
- "please complete this task"

## 2. Roles, circles, and actors

Two organizational shapes matter immediately:
- role: one actor is responsible for a domain
- circle: a team is jointly responsible for a domain

The key modeling choice is to describe both through the same responsibility canvas.

That gives the system a stable question to answer:
- who currently carries this domain

Instead of a fragile special case:
- is this a human-only flow
- is this an AI-only flow
- is this a team handoff

## 3. Agents as first-class actors

An agent is not just a tool wrapper.

In this model, an agent is another actor type inside the organization.
That means an agent can:
- carry responsibility for one or more domains
- act as a personal assistant for a specific user
- participate in the same operating processes as people
- be constrained by the same policy surface as the humans around it

A minimal actor reference looks like this:

```ts
type ActorRef = {
  kind: 'user' | 'agent';
  id: string;
  name?: string;
};
```

This matters because participation should not be modeled as "a list of user IDs plus some AI exceptions."

## 4. Shared operating entities

The agent layer becomes much more useful when it works over real organizational artifacts rather than isolated prompts.

Typical shared entities include:
- domains
- users
- tasks
- tensions or incoming problems
- agreements and policies
- proposals and decision artifacts
- development plans
- CRM records and workflow objects
- communication channels and messages

The important point is not the exact product schema.

The important point is that agents and humans should operate over the same system objects, so:
- work can be delegated without translation loss
- state changes are visible in the same operating system
- audit and accountability stay attached to the real artifact

## 5. Permission envelopes

Responsibility does not mean unlimited authority.

A useful public abstraction is a permission envelope:
- what the actor can read
- what the actor can write
- what tools it may use
- what monetary, operational, or risk limits apply
- what requires human approval
- how the run can be interrupted or stopped

This is stronger than vague prompt instructions because enforcement can happen:
- on the server
- in the runner
- in the UI
- in audit and reporting

## 6. Handoffs as boundary protocol

Cross-domain delegation should not turn agents into superusers.

That is why handoff matters as a protocol, not just as a social concept.

A handoff should preserve:
- who owned the work before
- who owns it now
- what context was passed forward
- what authority was and was not transferred
- what approvals or conditions still apply

In practice this is one of the biggest differences between:
- agent systems that look impressive in demos
- agent systems that survive contact with real organizations

## 7. One machine family, different configurations

A useful implementation pattern is to keep a shared runtime shape for agents, while varying:
- assigned domains
- policy scope
- tool surface
- escalation rules
- memory and retrieval scope

This avoids inventing a separate architecture for every agent flavor.

You get one runtime family with multiple organizational configurations:
- domain agent
- personal assistant
- specialist execution agent
- observer or analyst agent

## 8. Why this is not "just a copilot"

The differentiator is not only model quality.

The differentiator is that the system can explain:
- why the agent was allowed to act
- where the agent's responsibility stopped
- which domain policies applied
- why a human approval was required
- how a handoff changed accountability

That is what turns delegation into something governable.

## 9. Practical design rule

Do not let the AI layer invent an organization that the human layer does not recognize.

If people cannot understand the responsibility model, the agents will not be governable either.
