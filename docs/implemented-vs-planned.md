# Implemented vs planned

This repository is based on real production work, but it is intentionally not written as "everything here already exists exactly as described."

The goal of this page is to separate:
- what is already production-backed
- what is an active architecture direction
- what is intentionally left out of the public version

## Production-backed or already implemented in meaningful form

- org-aware responsibility modeling as a first-class way to describe agent context
- governance-first framing for human and agent collaboration
- async consent as a real workflow pattern around decision artifacts
- actor-level participation that includes agents, not only users
- separate runner or execution-surface patterns for agent work
- hybrid retrieval and knowledge tooling for organization data
- structured rich-result direction for AI answers instead of raw HTML blobs

## Active direction or currently evolving

- deeper Codex SDK-backed execution paths for specific agent modes
- richer org-aware analyst experiences on top of the same semantic tool surface
- dedicated semantic-search acceleration with vector-engine primary and fallback paths during rollout
- stronger AG-UI-aligned runtime layering above the current structured answer protocol
- further hardening of audit, observability, and multitenant runner behavior

## Intentionally not fully exposed here

- customer-specific workflows
- internal service names and private infrastructure topology in full detail
- secrets, credentials, connection setup, and deployment runbooks
- every product artifact and UI flow from the source system
- internal code references that would make this repo feel like a redacted monolith

## Why this split matters

Architecture repos become weak when they do one of two things:
- they are so abstract that they prove nothing
- they dump internal material without a clear public story

This repository is trying to stay in the middle:
- concrete enough to show a real system model
- selective enough to stay readable and safely public
