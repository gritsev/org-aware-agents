# Agentic RAG and rich results

This repository is primarily about org-aware agents, but retrieval and answer rendering matter because they shape what an agent can responsibly know and show.

In serious organizational systems, retrieval is not just a search feature.
It becomes part of the delegation model.

## 1. Why retrieval belongs here

If an agent is supposed to act inside responsibility boundaries, then its information access also needs boundaries.

That means retrieval should care about:
- organization scope
- domain scope
- entity type
- source traceability
- the difference between exact data and narrative context

Without this, the system falls back to "the model saw some text somewhere."

## 2. A useful split: structured tools and knowledge tools

One practical pattern is to separate:
- structured tools for exact counts, lists, filters, groupings, and entity lookups
- knowledge tools for text passages, protocol context, and cited evidence

That keeps the contract cleaner:
- use structured tools for exact answers
- use knowledge tools for context and source-backed narrative

This is especially important in organizational products where the user may ask:
- "how many open tasks do we have"
- "show the most overloaded users"
- "what was agreed about this policy"
- "where in the protocol was this discussed"

Those should not all hit the same retrieval path.

## 3. Agentic retrieval loop

A richer path is an agentic retrieval loop rather than a single retrieval shot.

A simplified public version looks like:
- search
- read
- refine
- answer

Typical steps include:
- keyword search
- semantic search
- chunk read for full evidence
- optional follow-up retrieval when the first pass is incomplete

The important idea is:
- answer from read evidence
- not from vague retrieval snippets alone

## 4. Hybrid retrieval with stable public contracts

The internal retrieval engine can evolve, but the public-facing contract should stay stable.

That means:
- keep `knowledge.search` and `knowledge.read` style contracts stable
- avoid leaking raw vector-engine semantics into user-facing tool surfaces
- preserve auditability around sources and follow-up reads

In the production systems behind these notes, hybrid retrieval combines:
- keyword search
- semantic search
- chunk reading

But the outside world should consume a knowledge surface, not a database implementation detail.

## 5. Semantic search as an engine, not a product contract

One current direction is to accelerate semantic search with a dedicated vector engine while keeping the rest of the retrieval plane stable.

The public-safe summary is:
- semantic search is moving toward a dedicated engine for better latency and stability
- one concrete direction is a ZVec-primary semantic-search path with pgvector-compatible fallback during rollout
- relational and chunk-based storage still remain critical for debugging, rebuilds, and exact reads
- fallback paths matter during rollout

This is a good example of why product contracts and engine choices should stay separate.

## 6. Why structured results matter

If the answer is important enough to act on, it often should not be rendered as a wall of text.

Useful structured result types include:
- tables
- lists
- KPIs
- charts
- compact markdown summaries

That lets the UI:
- render native components
- preserve machine-readable meaning
- separate transport from presentation
- keep source data inspectable

## 7. A2UI now, AG-UI plus A2UI later

One practical direction for rich AI answers is:
- direct structured payloads for the current UI contract
- with a future path toward a more general agent UI runtime

In the systems behind these notes, that means:
- structured answer payloads today through direct `A2UI`
- target platform direction of `AG-UI + A2UI`

The important architectural point is not the brand name.
It is that:
- the model should emit structured presentation data
- the backend should validate and normalize it
- the frontend should render it as a thin boundary, not as a second source of truth

## 8. Why this is part of governance

Retrieval and presentation are governance concerns when they affect:
- what evidence an agent can rely on
- how exact numbers are produced
- what the operator can verify
- whether UI hides or exposes the basis of a recommendation

That is why org-aware agents need not only policy and execution architecture, but also retrieval and answer architecture.
