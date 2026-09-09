# Trade Vault — MVP Scope

## Purpose

The MVP should prove that Trade Vault can become a collector's primary system of record **before** attempting physical custody, complex finance or every future marketplace feature.

## MVP objective

A user should be able to:

1. browse the catalogue without an account;
2. create an account and personal Vault;
3. add real physical collectibles;
4. organise them;
5. see useful market context;
6. wishlist/watch items;
7. search and discover;
8. use the product comfortably on mobile and desktop;
9. trust that their private collection data is actually private.

## Phase 0 — Foundation

Build first:
- monorepo;
- `apps/web`;
- `apps/ops` shell only;
- shared `packages/ui`;
- `packages/domain`;
- `packages/database`;
- environment strategy;
- CI;
- formatting/lint/typecheck/test commands;
- Supabase local/dev configuration;
- migrations;
- auth foundation;
- RLS/security tests;
- Obsidian Mint tokens/primitives;
- loading/error/empty-state foundations;
- feature flags;
- basic logging/observability.

No marketplace payment or physical Vault logic yet.

## Phase 1 — Identity & onboarding

- guest browsing;
- email/Google/Apple auth where practical;
- user;
- profile;
- automatic personal ownership account;
- username;
- country/currency;
- favourite TCGs;
- interests;
- privacy defaults;
- settings/security shell.

## Phase 2 — Catalogue & search

- TCG catalogue;
- sets;
- catalogue items;
- card printings;
- sealed products;
- language;
- rarity;
- grading companies/scales;
- external provider mappings;
- canonical images;
- provider adapters;
- fuzzy search;
- item/set pages;
- release dates.

Data model supports all six target TCGs. Provider ingestion may be enabled game-by-game based on data quality.

## Phase 3 — My Vault

- one asset per physical item;
- raw/graded/sealed creation;
- Quick Add;
- batch quantity creates individual rows;
- acquisition method/date;
- private acquisition cost;
- condition;
- grader/grade/cert;
- private notes;
- front/back images;
- tags;
- binders;
- favourites;
- private owner storage locations;
- grid/list/binder views;
- asset timeline;
- private personal valuation.

## Phase 4 — Portfolio & market read

- market instruments;
- ingestion interfaces;
- current estimate;
- last sale/recent evidence where available;
- AU vs Global;
- confidence;
- sold vs active distinction;
- short price history;
- portfolio total;
- cost basis;
- basic gain/loss;
- value by TCG/set.

Retain raw observations and pricing model versions.

## Phase 5 — Wishlist / Watchlist / Explore

- structured wishlist;
- watchlist;
- limited alerts;
- saved-search basics;
- Explore;
- trending framework;
- new releases;
- upcoming set binder;
- Recently Viewed.

## Phase 6 — AI-assisted intake beta

Only after ordinary add flow is solid:
- server-side recognition gateway;
- image upload;
- candidate matches;
- confidence;
- user confirmation;
- prediction history.

Continuous camera scanning follows when recognition quality is adequate.

## Explicitly not in initial MVP

Do not build production physical operations yet:
- physical Vault;
- facility verification workflow;
- grading submission;
- high-value middleman;
- physical locations;
- insurance claims.

Do not build full marketplace finance yet:
- Stripe Connect settlement;
- buyer protection automation;
- chargeback accounting;
- multi-seller checkout.

Do not build full community yet:
- generic DMs;
- user-created groups;
- dealer storefronts;
- deep achievements;
- offline Card Show mode.

Do not build unnecessary infrastructure:
- microservices;
- Kafka;
- Kubernetes;
- dedicated search cluster;
- warehouse.

## MVP success criteria

A serious collector can reasonably say:

> “I could move my collection into Trade Vault and use this as my everyday collection and market app.”

Before adding payment/custody risk, look for repeated collection use, portfolio use, wishlist/watchlist activity, healthy search, willingness to migrate real collections, acceptable data quality and good mobile performance.

## MVP invariants

Even in MVP:
- one physical item = one asset;
- canonical Trade Vault IDs;
- account/organisation separation;
- ownership ledger architecture;
- cost basis history;
- current state + event history;
- server/database privacy;
- version-controlled migrations;
- idempotent ingestion;
- provider abstraction;
- semantic design tokens.
