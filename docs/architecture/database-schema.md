# Trade Vault — Formal Database Schema

This document defines the intended relational model. Version-controlled migrations remain authoritative for implementation.

## 1. Identity

### `identity.users`
Private authenticated human.

Key fields:
- `id uuid pk`
- `auth_user_id uuid unique`
- `primary_email`
- `identity_verification_status`
- `account_status`
- timestamps

### `identity.profiles`
Public profile:
- `user_id pk/fk`
- `username`
- `display_name`
- `avatar_media_id`
- `bio`
- `country_code`
- `region`
- privacy settings

Username uniqueness is case-insensitive.

### `identity.accounts`
Ownership/commercial entity:
- PERSONAL
- ORGANISATION

Registration automatically creates one PERSONAL account.

### `identity.account_memberships`
- `account_id`
- `user_id`
- `role_code`
- `status`

### `identity.organisations`
- account
- legal/trading name
- ABN
- verification status
- branding

### `identity.addresses`
Mutable address book.

### `identity.address_snapshots`
Immutable transaction address copy.

## 2. Catalogue

### `catalogue.tcgs`
### `catalogue.product_lines` — optional
### `catalogue.sets`

### `catalogue.items`
Base marketable entity.

Types:
- CARD_PRINTING
- SEALED_PRODUCT

Common fields:
- item type
- TCG
- name
- release/status/media
- JSONB only for irregular metadata

### `catalogue.card_concepts`
Optional discovery grouping.

### `catalogue.card_printings`
- catalogue item
- set
- concept
- `card_number text`
- rarity
- language
- printing attributes

### `catalogue.sealed_products`
- catalogue item
- set/product type
- region/language
- packaging

### `catalogue.product_components`
Optional product composition.

### `catalogue.external_provider_mappings`
- provider
- entity type
- Trade Vault entity ID
- external ID
- URL
- sync time

Provider/entity/external ID should be unique.

### `catalogue.languages`
Controlled codes.

### `catalogue.rarities`
TCG-specific rarity catalogue.

### `catalogue.grading_companies`
### `catalogue.grade_scales`
### `catalogue.grade_values`

Allows BGS 10 Pristine and BGS 10 Black Label to remain distinct.

## 3. Collection

### `collection.assets`
One row per physical collectible.

Key fields:
- `id uuid pk`
- `owner_account_id`
- `catalogue_item_id`
- `asset_type`
- `current_condition_code`
- `current_grading_certification_id`
- `current_commerce_state`
- `current_trade_state`
- `current_custody_state`
- `current_cost_basis_minor`
- `current_cost_basis_currency`
- personal valuation
- acquisition metadata
- `version`
- `archived_at`
- timestamps

Private untouched assets do not require public business IDs until externally referenced.

### Subtypes
- `collection.raw_asset_details`
- `collection.graded_asset_details`
- `collection.sealed_asset_details`

### `collection.ownership_events`
Append-oriented provenance:
- asset
- from account
- to account
- event type
- related order/trade/external transfer
- timestamp
- idempotency key

Current owner update and ownership event happen atomically.

### `collection.cost_basis_events`
Private history.

### `collection.personal_valuation_events`
Private history.

### `collection.condition_observations`
- asset
- condition
- source
- verification report
- notes
- observed time

### `collection.grading_certifications`
- asset
- grader
- grade value
- cert
- status
- graded date
- remote verification
- superseded date

### `collection.asset_images`
- asset
- role
- source
- storage key
- content/perceptual hashes
- moderation
- evidence lock

### `collection.asset_events`
User-facing general timeline.

### Organisation
- `collection.binders`
- `collection.binder_assets`
- `collection.tags`
- `collection.asset_tags`
- `collection.favourites`
- `collection.user_storage_locations`

Owner storage locations are private-only.

## 4. Market

### `market.markets`
Flexible geography: AU, US, JP, EU, GLOBAL.

### `market.instruments`
- catalogue item
- presentation
- grader
- grade
- market

### `market.observations`
- instrument
- source/source record
- observation type
- original price/currency
- conversion rate
- converted amount/currency
- geography
- occurred/ingested time
- match confidence
- trust weight
- exclusion state
- raw metadata

### `market.estimates`
Timestamped:
- instrument
- value
- currency
- confidence
- pricing model version
- observation counts
- calculated time

Never overwrite historical estimates.

### Other
- `market.wishlist_entries`
- `market.watchlist_entries`
- `market.price_alerts`
- `market.saved_searches`

## 5. Commerce

### `commerce.listings`
One asset may have many historical listings.

States:
- DRAFT
- ACTIVE
- RESERVED
- SOLD
- CANCELLED
- EXPIRED
- UNDER_REVIEW
- SUSPENDED

### `commerce.listing_assets`
Collector listing normally one asset. Dealer inventory offers can later map multiple interchangeable eligible assets.

### `commerce.reservations`
- listing
- asset
- buyer
- checkout
- expiry
- state

Reservation blocks conflicting sale/trade/withdrawal activity.

### Offers
- `commerce.offer_threads`
- `commerce.offer_revisions`

Immutable revisions with expiry.

### `commerce.checkouts`
Parent for eventual multi-seller checkout. One transactional currency per checkout.

### `commerce.orders`
Seller-specific order:
- checkout
- buyer/seller
- commercial state
- currency
- subtotal
- fee snapshot
- shipping snapshot
- policy versions
- version
- timestamps

### `commerce.order_items`
- order
- asset
- listing snapshot
- purchase amount
- item state
- ownership transfer state

### `commerce.listing_snapshots`
Immutable accepted listing evidence.

### Fulfilment
- `commerce.fulfilments`
- `commerce.shipments`
- `commerce.shipment_events`

### Dispute/returns
- `commerce.disputes`
- `commerce.dispute_evidence`
- `commerce.returns`

## 6. Trading

### `trading.trades`
Overall trade case.

### `trading.trade_parties`
Exactly two enforced initially.

### `trading.trade_versions`
Immutable sent/counter versions.

### `trading.trade_version_assets`
Includes trade-facing asset snapshot.

### `trading.trade_cash_adjustments`
One payment direction per accepted version.

### `trading.trade_fulfilments`
Modes:
- DIRECT
- VERIFIED
- LOCAL
- VAULT_TO_VAULT

Direct trade has two shipment legs. Verified trade can have inbound/outbound legs. Ownership swap occurs atomically.

## 7. Verification / Trust

### `trust.verification_cases`
Operational workflow.

### `trust.verification_expected_items`
Frozen expected identity.

### `trust.verification_findings`
Structured identity/authenticity/condition findings.

### `trust.verification_reports`
Permanent report:
- public ID
- overall result
- methodology version
- issued date
- revoked date
- superseded report

### `trust.risk_signals`
Examples:
- DUPLICATE_CERT
- REUSED_IMAGES
- NEW_DEVICE_HIGH_VALUE
- CHARGEBACK_HISTORY
- MARKET_MANIPULATION_PATTERN

## 8. Custody

### `custody.custodians`
Owner/Trade Vault/carrier/grader as needed.

### Locations
- `custody.vault_sites`
- `custody.vault_zones`
- `custody.vault_containers`
- `custody.vault_slots`

Users never see exact internal location.

### Inbound
- `custody.inbound_shipments`
- `custody.inbound_shipment_items`

Supports expected/unmatched items.

### `custody.custody_events`
Append-oriented movement:
- asset
- previous/new custodian
- from/to location
- operator
- timestamp
- reason
- device/scan
- related case/order/trade

### `custody.withdrawal_requests`
Own workflow with immutable request snapshot.

### `custody.incidents`
Missing/damaged/wrong dispatch etc.

## 9. Finance

### `finance.provider_accounts`
Maps Trade Vault accounts to Stripe/other providers.

### `finance.payments`
Provider payment state.

### Ledger
- `finance.ledger_accounts`
- `finance.ledger_transactions`
- `finance.ledger_entries`

Double-entry-style internal truth.

Money = integer minor units + currency.

### Settlement
- `finance.seller_payables`
- `finance.payouts`
- `finance.payout_allocations`
- `finance.settlement_holds`

### Adjustments
- `finance.refunds`
- `finance.chargebacks`
- `finance.service_charges`

### Subscriptions
- `finance.subscriptions`
- `finance.subscription_entitlements`

Trade cash adjustments use the same finance engine.

## 10. Community

- `community.posts`
- `community.post_attachments`
- `community.comments`
- `community.reactions`
- `community.follows`
- `community.showcases`
- `community.conversations`
- `community.messages`

Transaction messaging should be distinguishable from ordinary community messaging.

## 11. Notifications

- `notifications.notification_events`
- `notifications.preferences`
- `notifications.deliveries`

Store event/type + structured payload. Render per channel.

## 12. Operations

- `operations.staff_users`
- `operations.roles`
- `operations.permissions`
- `operations.staff_role_assignments`
- `operations.approval_requests`
- `operations.user_reports`
- `operations.enforcement_actions`
- `operations.audit_events`
- `operations.outbox_events`

Dual approval required for defined high-risk manual actions.

## 13. Mechanics

Use:
- UUID internal PKs;
- friendly non-sequential public references;
- check constraints/enums for genuinely fixed technical states;
- lookup tables for evolving business concepts;
- JSONB only for irregular metadata;
- `timestamptz`;
- integer minor units for money;
- version fields on critical mutable aggregates;
- unique idempotency keys;
- case-insensitive username index;
- derived search projection/index separate from canonical normalised data.

## 14. Deletion

Hard-delete only genuinely untouched private accidental assets.

Meaningful historical records are archived/retained according to policy.

Personal information may be anonymised/deleted while required transaction/evidence records remain.

## 15. Golden rule

> **An important historical event is added, not rewritten.**
