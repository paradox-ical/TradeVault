# AGENTS.md — Trade Vault

This file is the map for coding agents. Keep it short. Detailed requirements live under `docs/`.

## Read before changing code

Read, in this order:

1. `ARCHITECTURE.md`
2. `docs/product/master-blueprint.md`
3. `docs/product/mvp-scope.md`
4. `docs/product/roadmap.md`
5. `docs/design/visual-design-system.md`
6. `docs/architecture/domain-model.md`
7. `docs/architecture/database-schema.md`
8. `docs/architecture/state-machines.md`
9. `docs/architecture/security-model.md`
10. `docs/decisions/locked-decisions.md`

For the first Codex session, follow `docs/prompts/000-first-codex-prompt.md`.

## Core stack

- Next.js
- React
- TypeScript
- PostgreSQL / Supabase
- Monorepo
- Modular monolith
- Responsive web application
- PWA capabilities
- Separate collector-facing and operations applications

Pin exact dependency versions during repository bootstrap. Do not silently jump major versions without documenting why.

## Expected repository shape

```text
apps/
  web/
  ops/
packages/
  ui/
  domain/
  database/
  catalogue/
  payments/
  notifications/
  config/
docs/
  product/
  design/
  architecture/
  decisions/
  plans/
  prompts/
```

## Non-negotiable invariants

1. **One physical collectible = one asset record.**
2. Payment, order, fulfilment, ownership and seller settlement are separate concepts.
3. Ownership and physical custody are separate concepts.
4. Important historical events are appended rather than silently rewritten.
5. External provider IDs never become canonical Trade Vault IDs.
6. Sensitive mutations run through trusted server-side workflows.
7. Private data is enforced by database/server authorisation, not frontend hiding.
8. Money is integer minor units plus currency. Never floating point.
9. Critical workflows are idempotent.
10. Meaningful domain events use a transactional outbox.
11. High-value transactions may require Trade Vault physical verification.
12. Verification is not grading.
13. Continuous custody is stronger than historical verification.
14. If Trade Vault claims custody, the system must know the responsible custodian and latest reconciled physical location or active transit process.
15. Every cent entering, leaving, owed by or owed to Trade Vault must be explainable through ledger entries.
16. Production operations should be performed through the audited ops application, not ad-hoc SQL.

## Product and architecture changes

If implementation convenience conflicts with a locked decision:

- preserve the documented decision;
- explain the conflict;
- propose a change explicitly;
- update docs only after the change is accepted.

Do not silently weaken invariants.

## Build discipline

- Prefer small vertical slices over broad partial implementations.
- Add migrations to version control.
- Add tests for critical domain transitions.
- Add RLS/authorisation tests for private data.
- Use feature flags for intentionally deferred capabilities.
- Do not add microservices, Kafka, Kubernetes, Elasticsearch/OpenSearch, a warehouse or other heavy infrastructure until measured need exists.

## Definition of done

A feature is not done until its relevant domain rules, migration, authorisation, UI states, loading/error/empty states, accessibility, tests, documentation and observability are complete.
