# Recommender Protocol (Project Outline)

A platform-agnostic recommendation protocol + reference engine that lets users own their ranking layer across any content source they already follow. The goal is total transparency, local-first by default, and user-controlled objectives such as depth, novelty, calm, and learning.

## Core Promise
- User-owned ranking for sources the user already follows
- Transparent scoring with explainable factors
- Local-first by default, opt-in hosted execution
- Open adapters so platforms can be plugged in without rewriting the engine

## Product Shape
- Protocol: shared data contracts and ranking/explainability rules
- Engine: reference implementation that consumes the protocol
- Adapters: platform-specific bridges that map data into the protocol

## Principles
- User control over objectives and exploration
- Clear, inspectable scoring breakdowns
- Privacy-preserving by default
- Deterministic by default, with optional exploration toggle

## Scope (v0)
- Inputs: feeds and platform adapters (e.g., RSS, YouTube channel feeds)
- Outputs: ranked list with explanations + discovery suggestions
- No hosting of content; only ranking and curation

## Protocol Surface (v0)

### Entities
- Source
- Item
- User
- Interaction
- Feature
- Objective
- Score
- Explanation
- PolicyDecision

### Interaction Types
- view
- watch_time
- skip
- save
- not_interested
- mute_source
- topic_follow

### Objectives
- depth
- novelty
- calm
- learning
- custom_weights

### Explainability Contract
- Each scored item must return a breakdown of contributing factors
- Factors include score deltas, weights, and evidence pointers

### Policy Hooks
- User-level blocks (creator or source bans)
- Protocol-level policy updates for gaming mitigation
- Audit log of policy changes

## API Shape (Conceptual)
- Ingest sources and items
- Record interactions
- Rank items for a user + objective
- Recommend adjacent sources based on user intent
- Export user profile and graph

## Execution Model
- Local engine runs entirely on-device
- Hosted engine is optional and opt-in
- Same protocol and data model for both

## Adapters
- Map platform data to protocol entities
- Translate platform metadata to features
- Sync user interactions into protocol format
- Render ranked results back into platform UI

## Anti-Gaming Strategy (High-Level)
- User can hard-ban creators or sources
- System adapts policy rules over time to reduce manipulation
- Transparency for users, but policy logic may evolve to reduce exploitability

## Open Questions
- Protocol format choice: JSON/REST vs protobuf/gRPC
- Performance targets by platform and scale
- Discovery strategy: adjacent sources vs topic exploration
- Hosted execution: trust model, privacy guarantees, cost model

## Next Steps
- Decide protocol format and versioning strategy
- Draft formal schema and reference test fixtures
- Define a minimal reference engine spec
- Identify first adapter target (YouTube, RSS)
