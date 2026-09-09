# First Codex 6 Astra Prompt — Trade Vault

Copy the prompt below into the **first serious Codex session** for this repository.

---

You are acting as the lead software engineer for a new product called **Trade Vault**.

Trade Vault is a long-term trading-card collection, market intelligence, marketplace, trading, verification and physical-custody platform.

**Do not begin implementing product features yet.**

Your first task is to understand the product, architecture and design requirements contained in this repository and create a technically rigorous implementation plan.

## Authoritative documentation

Read these documents before proposing any implementation:

- `AGENTS.md`
- `ARCHITECTURE.md`
- `docs/product/master-blueprint.md`
- `docs/product/mvp-scope.md`
- `docs/product/roadmap.md`
- `docs/design/visual-design-system.md`
- `docs/architecture/domain-model.md`
- `docs/architecture/database-schema.md`
- `docs/architecture/state-machines.md`
- `docs/architecture/security-model.md`
- `docs/decisions/locked-decisions.md`

Treat these files as the current source of truth.

If implementation convenience conflicts with an explicit product or architectural decision, preserve the documented decision unless there is a strong technical reason not to.

If you believe a documented decision should change, explain the issue and propose the change. Do not silently change it.

## Architecture

Trade Vault uses a deliberately scalable foundation rather than either a disposable prototype or premature microservices.

The intended architecture is:

- Next.js
- React
- TypeScript
- PostgreSQL / Supabase
- modular monolith
- monorepo
- responsive web application
- PWA capabilities
- separate collector-facing and operations applications
- domain-driven package boundaries
- trusted server-side execution for sensitive transactions
- RLS/server authorisation for private data
- version-controlled SQL migrations
- explicit state machines
- append-oriented ownership, custody, verification, financial and audit history
- first-class idempotency
- transactional outbox for meaningful domain events
- provider abstractions for payments, AI and external catalogue/market services

Do not introduce microservices, Kafka, Kubernetes, Elasticsearch/OpenSearch, a dedicated warehouse or comparable operational complexity unless the current scope genuinely requires it.

## Critical invariants

These must not be violated:

1. **One physical collectible = one asset record.**
2. Payment, order, fulfilment, ownership and seller settlement are separate concepts.
3. Ownership and physical custody are separate concepts.
4. Important historical events are appended rather than silently rewritten.
5. External provider IDs never define Trade Vault canonical identity.
6. Sensitive mutations are server-authoritative.
7. Private financial and collection data must be protected by database/server authorisation rather than merely hidden in the UI.
8. Money uses integer minor units plus currency.
9. Important retries must be idempotent.
10. Critical state changes publish meaningful domain events through a transactional outbox.
11. High-value transactions may require Trade Vault physical verification.
12. Trade Vault Verification is not numerical grading.
13. A historically verified owner-held card is not equivalent to a continuously Trade Vault-held card.
14. If Trade Vault claims physical custody, the system must identify its responsible custodian and latest reconciled physical location or active transit workflow.
15. Every cent entering, leaving, owed by or owed to Trade Vault must be explainable through immutable financial entries linked to the business event that caused it.
16. Production operations should occur through an audited operations app, not ad-hoc database editing.

## Visual direction

The approved default visual identity is **Obsidian Mint**.

Read:

`docs/design/visual-design-system.md`

Do not improvise an unrelated visual style.

Trade Vault should feel:

- dark
- premium
- secure
- restrained
- collector-first
- modern
- polished

Use tasteful Liquid Glass-inspired layering, smooth microinteractions and subtle depth without sacrificing performance, accessibility or information density.

Card artwork should provide most of the visual colour.

Use semantic design tokens rather than scattering literal colour values through feature components.

## MVP discipline

Read `docs/product/mvp-scope.md` carefully.

Do not begin by building the final product.

The early implementation should prove:

- repository quality;
- authentication;
- canonical catalogue;
- search;
- private My Vault;
- collection intake;
- portfolio/market read;
- wishlist/watchlist;
- responsive Obsidian Mint UI.

Marketplace finance, physical verification and physical Vault operations are intentionally deferred until their roadmap stage.

Create interfaces/abstractions now only where they prevent future architectural rewrites. Do not create fake implementations of future physical operations.

## Your task

Inspect the full repository and documentation.

Then create:

`docs/plans/active/000-foundation-plan.md`

The plan must include:

1. Proposed repository structure.
2. Exact bootstrap sequence.
3. Recommended dependencies and why each is needed.
4. Versions you intend to pin.
5. Environment/configuration requirements.
6. Supabase/Postgres local-development strategy.
7. Database migration strategy.
8. Authentication architecture.
9. Authorisation/RLS architecture.
10. Design-system/component architecture.
11. Initial domain package boundaries.
12. MVP phases in dependency order.
13. Testing strategy.
14. CI quality gates.
15. Logging/observability baseline.
16. Security controls required immediately.
17. Feature flags/interfaces to create now for deferred capabilities.
18. Capabilities that must deliberately **not** be implemented yet.
19. Contradictions, ambiguities or missing technical decisions in the documentation.
20. Major implementation risks.
21. Definition of done for the first foundation milestone.

Also propose any necessary changes to:

- `AGENTS.md`
- `ARCHITECTURE.md`

but **do not make those changes automatically** during this planning task unless they are trivial formatting corrections.

## Planning expectations

Prefer small vertical slices.

The first implementation milestone should establish a high-quality foundation rather than a broad set of half-built screens.

Do not write hundreds of application files during this task.

Do not implement user-facing product features yet.

Do not introduce speculative infrastructure because it might be useful at very large scale.

Prefer boring, well-understood technology.

Where the docs intentionally say a feature comes later, respect that sequencing.

## Final response

At the end of this task, summarise:

- what you learned about Trade Vault;
- what you believe the MVP is;
- the repository structure you recommend;
- the first implementation milestone;
- the major risks;
- any decisions you need from me before implementation begins.

Then stop and wait for review of the plan before beginning implementation.

---
