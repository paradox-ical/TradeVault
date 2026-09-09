# Trade Vault — Product & Build Roadmap

No dates are implied. This is the recommended dependency order.

## Stage 0 — Repository Foundation

Outcome: the project can be safely developed by multiple agents/developers without architecture drift.

Build monorepo, docs, design tokens, CI, environments, database foundation, migrations, auth skeleton, authorisation patterns, tests, feature flags and domain package boundaries.

## Stage 1 — Collection MVP

Outcome: Trade Vault is useful without a marketplace.

Build guest browsing, signup/onboarding, personal account, catalogue, search, My Vault, raw/graded/sealed, images, binders/tags/favourites, private acquisition data, asset timeline, responsive web and PWA baseline.

## Stage 2 — Market Intelligence MVP

Outcome: collections have useful market context.

Build market instruments, observations, AU/Global pricing, estimates, confidence, recent sales, portfolio totals, wishlist/watchlist, alerts, Explore and releases.

## Stage 3 — AI Intake & Migration

Outcome: moving a collection into Trade Vault becomes materially faster.

Build image recognition, slab metadata recognition, continuous scan, CSV, migrations and batch review/error resolution.

## Stage 4 — Marketplace Beta

Outcome: users can safely list and buy owner-held assets.

Build identity verification for sellers, payout onboarding, listing, reservation, checkout, orders, payment abstraction, Stripe Connect implementation, same-seller cart, shipping, delivery, inspection, seller payable/payout, immutable snapshots, dispute baseline, finance ledger, reconciliation and marketplace messaging.

Do not launch until security, idempotency, concurrency and reconciliation tests pass.

## Stage 5 — Trading Beta

Outcome: trading is a first-class transaction, not a DM workaround.

Build trade states/preferences, proposals/revisions, soft holds, atomic acceptance locking, direct fulfilment, local QR handoff, cash adjustments, Trade Finder and reputation.

Mandatory physical verification remains feature-flagged until operational infrastructure exists.

## Stage 6 — Community V1

Profiles, follows, showcases, asset-driven posts, reactions, comments, privacy-controlled messaging, local discovery, platform-created groups, basic achievements, collector QR and online Card Show Mode.

## Stage 7 — Trade Vault Verification Pilot

Requires legal advice, insurance, secure facility, operator procedures, staff controls and incident processes.

Software: inbound shipments, expected assets, intake evidence, reconciliation, verification cases/findings/reports, public lookup, verification IDs, methodology versioning, revocation and selected high-value routing.

## Stage 8 — Physical Vault Pilot

Build sites/zones/containers/slots, scanning, custody events, reconciliation, withdrawals, picking/packing, dual-control high-value operations, insurance snapshots and vault-held sale/transfer.

## Stage 9 — Grading Hub

Build grading submission, pre-grade, intake imaging, third-party custodian tracking, PSA/BGS/CGC workflows, return reconciliation and post-grade actions.

## Stage 10 — Dealer Platform

Build organisation onboarding, business verification, staff permissions, storefront, bulk inventory, inventory offers, commercial rates, feeds/API and analytics.

## Stage 11 — Scale / International

Only when justified:
- additional settlement currencies;
- international shipping;
- more TCGs;
- multi-seller checkout;
- dedicated search;
- warehouse/BI;
- native apps;
- more Vault sites;
- professional data API.

## What not to do

Do not:
- build physical operations before collection product-market fit;
- call delayed marketplace funds “escrow” without legal structure;
- let provider objects replace internal accounting;
- let external catalogue APIs define canonical identity;
- publicly expose cost basis;
- add heavy infrastructure because it sounds scalable;
- let an agent silently contradict locked decisions.
