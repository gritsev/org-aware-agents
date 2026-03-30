# Responsibility model

## Why agent context should start from responsibility, not from a giant prompt

In many systems, an agent receives:
- a role description
- a task
- maybe some tools

That is usually not enough.

In an organization, an actor needs a stable operating context:
- what area it is responsible for
- where its authority ends
- who its internal and external customers are
- what outcomes it is expected to produce
- what constraints and metrics apply

Without this, agents become "smart interns with admin access".

## Core primitives

### Domain

A domain is an explicit area of responsibility.

It should define:
- purpose
- authority boundaries
- customers and expected outcomes
- suppliers and dependencies
- metrics and constraints

### Role

A role is a single actor responsible for a domain.

### Circle

A circle is a team jointly responsible for a domain.

The key design move is to model both role and circle through the same responsibility canvas.

That means:
- humans and agents can consume the same operating language
- the system can treat "who owns this domain" as a configuration question, not a special case

## What becomes executable

Once responsibility is explicit, the agent layer can derive:
- readable scope
- allowed tool surfaces
- escalation paths
- handoff targets
- approval requirements
- audit expectations

This is a much stronger foundation than "be helpful and do not make mistakes".

## A simple rule

Do not ask an agent to act outside a responsibility model that a human in the same system would also understand.

