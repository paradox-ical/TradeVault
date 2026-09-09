# Trade Vault — Architecture

## 1. Goal

Trade Vault uses a **deliberately scalable modular monolith**.

Avoid both:
- disposable prototype architecture that guarantees a rewrite; and
- premature enterprise complexity that slows learning.

> **Boring, proven technology + strong domain boundaries + complexity only when justified.**

## 2. Initial platform

- Responsive web application
- PWA capabilities
- Mobile-first capture/card-show workflows
- Desktop-first bulk management/operations
- Native apps later

## 3. Application topology

```text
apps/web        collector-facing app
apps/ops        internal operations app
packages/ui     shared design system
packages/domain business entities/rules/state transitions
packages/database schema, migrations, generated types
packages/catalogue canonical catalogue + provider adapters
packages/payments payment abstraction + finance integration
packages/notifications notification routing/delivery
packages/config shared configuration and feature flags
```

## 4. Core technology

- Next.js + React + TypeScript
- PostgreSQL as primary operational database
- Supabase for managed Postgres/Auth/Storage/Realtime/Functions where appropriate
- Version-controlled SQL migrations
- Trusted server-side workflows for sensitive operations
- RLS/grants for user-scoped access

## 5. Access model

### RLS-safe user-scoped operations

Examples:
- public catalogue reads;
- public profile reads;
- own binders;
- own collection reads.

### Trusted server operations

Examples:
- order creation/completion;
- trade acceptance;
- ownership transfer;
- refunds;
- settlement;
- verification reports;
- custody changes;
- staff actions.

## 6. Domains

- Identity
- Catalogue
- Collection
- Market Data
- Commerce
- Trading
- Finance
- Trust
- Verification
- Grading
- Custody
- Community
- Notifications
- Operations

Modules communicate through explicit interfaces and meaningful internal events.

## 7. Domain events

Examples:
- `asset.created`
- `asset.ownership_transferred`
- `listing.published`
- `order.paid`
- `order.completed`
- `trade.accepted`
- `trade.completed`
- `verification.completed`
- `custody.asset_received`

Meaningful events use a transactional outbox.

## 8. Current state + history

Store current state for fast querying and append-oriented history explaining how it happened.

Critical histories:
- ownership;
- cost basis;
- custody;
- verification;
- finance;
- transaction snapshots;
- staff audit.

Corrections create new correction/reversal events rather than rewriting history.

## 9. Concurrency and idempotency

Critical mutable aggregates use optimistic version fields where useful:
- assets;
- listings;
- orders;
- trades;
- verification cases;
- withdrawals.

First-class idempotency applies to payment webhooks, order completion, ownership transfer, trade completion, payouts, custody events, market ingestion and notifications.

## 10. Search

Start with PostgreSQL full-text/trigram/fuzzy search plus derived search documents. Move to dedicated search only when justified.

## 11. Jobs

Start with managed cron/queue capabilities for:
- catalogue sync;
- price ingestion;
- estimates;
- AI recognition;
- cert checks;
- notifications;
- risk checks;
- settlement release;
- stale reservation cleanup.

Keep interfaces portable.

## 12. Storage

Separate access/retention policies for catalogue imagery, user asset media, community media, verification evidence, grading scans, dispute evidence and operational media.

## 13. AI

AI is server-side through internal abstractions such as `CardRecognitionService`.

Store model prediction/confidence and user-confirmed/corrected result separately.

## 14. Payments

Use a `PaymentProvider` abstraction. Initial provider is Stripe/Stripe Connect.

Trade Vault maintains its own financial ledger. Provider objects are references, not the sole source of truth.

## 15. Environments

- Development
- Staging
- Production

Preview environments when practical.

## 16. Testing

- Unit: rules, state machines, fees, pricing
- Integration: DB/payment/domain workflows
- E2E: representative vertical journeys
- Security/RLS: cross-user isolation
- Idempotency: duplicate webhooks/jobs
- Concurrency: competing purchase/trade attempts

## 17. Deferred infrastructure

Do not start with microservices, Kafka, Kubernetes, Elasticsearch/OpenSearch, a warehouse, service mesh or a complex distributed event bus.

## 18. Maxim

> **Current state tells us what is true now. Historical ledgers tell us how it became true.**
