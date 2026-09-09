# Trade Vault — Locked Decisions

Concise reference of settled product/architecture choices.

## Product foundation

- Australia-first, global-ready.
- Initial TCGs: Pokémon, MTG, Yu-Gi-Oh!, One Piece, Lorcana, Riftbound.
- Raw + graded + sealed in digital My Vault.
- Collection is the platform.
- One physical collectible = one asset.
- Detailed-first entry with compact Quick Add.
- Binders + tags + favourites.
- User-defined set completion.
- Raw condition: Mint / Near Mint / Excellent / Good / Poor.
- Owner-held raw sale/trade requires front + back photos.
- Camera, image upload, barcode, batch, CSV/import.
- AI assists; user confirms.
- Full asset timeline.

## Market

- Trade Vault market estimate + supporting metrics.
- Australia + Global market views.
- Preserve original transaction currency.
- Completed sales weighted above active asks.
- Inspectable outlier filtering.
- High / Medium / Low confidence.
- One general raw headline value initially.
- Private personal valuation.
- Price alerts.
- Historical data where available.
- Sold evidence visibly separated from asking prices.

## Marketplace

- Fixed price + offers + trade availability.
- Collection-first listing; marketplace-first fallback creates asset.
- Hybrid catalogue/listing browsing.
- Smart one-page listing.
- Contextual seller pricing assistance.
- Trade Vault handles payment.
- Seller settlement after delivery/inspection.
- Defined buyer protection.
- Integrated + seller-managed tracked shipping.
- In-platform local pickup.
- General location only.
- Grader cert verification where possible.
- Working fee target around 4% total, subject to modelling.
- No ordinary listing fee.
- Same-seller cart first, multi-seller later.
- Historical sold records retained.

## Trading

- Not for Trade / Open to Offers / Available for Trade.
- Structured wants + free text.
- Multi-asset trades + one-direction cash adjustment.
- Full immutable proposal revisions.
- Accepted trade atomically locks all assets.
- Direct and Verified fulfilment.
- High-value threshold can mandate Trade Vault verification.
- Direct trade completes only when both sides fulfil.
- Vault-to-Vault uses digital ownership swap.
- Trade Finder is core.
- Optional automatic match alerts.
- Seller/trader reputation separated.
- Structured trade feedback.

## Verification / Vault

- Hybrid risk/value verification threshold.
- High-value graded cards still physically checked.
- Verification = authenticity + identity + documented condition, not numerical grade.
- Detailed report + Pass/Review/Fail.
- Public non-sequential verification ID.
- Verification record permanent; custody continuity separate.
- Long-term grading hub.
- AI + optional human pre-grade.
- User chooses post-grade ship/store/sell/trade.
- Initial physical Vault: raw + graded.
- Hybrid storage pricing.
- Market vs declared vs insured value separated.
- Buyer chooses keep vaulted or withdraw.
- Public verification lookup.
- External vaulted ownership transfer.
- High-value sale and trade both subject to verification.
- Verification intended as authentication/provenance brand.
- Physical custody must always have responsible custodian + latest reconciled location or active transit process.

## Community

- For You / Following / TCGs / Showcases.
- Asset-driven content + limited general collector posts.
- Optional pickup sharing.
- User-controlled public asset fields.
- Financial totals hidden by default.
- Follower model.
- Privacy-controlled DMs.
- Comments with per-post disabling.
- Love / Heat / Trade? / Grail reactions.
- Trade reaction can be functional.
- Showcase.
- Achievements without spending pressure.
- Favourite TCGs and collector interests.
- Platform-created groups first.
- Opt-in regional discovery.
- No wealth leaderboard.
- Dealer/business profiles.
- Card Show Mode + collector QR.

## Monetisation

- Unlimited basic collection free.
- Free recent history; Pro deeper.
- Basic analytics free; advanced Pro.
- Limited free alerts; higher/unlimited Pro.
- Limited free AI; higher Pro.
- Imports free.
- Trade Finder core free; advanced Pro.
- Meaningful Pro fee discount.
- Small Vault allowance in Pro.
- Pro verification discount.
- Pro is not a trust badge.
- Free / Pro / Dealer.
- Monthly + discounted annual.
- Target Pro positioning A$10–15/month, subject to modelling.
- Transparent fees.
- Mandatory verification priced separately.
- Dealer subscription + lower commercial rates.
- Clearly labelled promoted listings allowed.
- No broad ad clutter; limited relevant partnerships.
- Affiliate disclosure required.
- Long-term Data/API business.

## UX

- Guest browse before signup.
- Email + Google + Apple; passkeys later.
- Short onboarding.
- Optional collection-size question.
- First-action choice.
- Universal intelligent fuzzy search.
- Personalised ranking but exact match wins.
- Explore separate from Marketplace.
- Composite trending score.
- Liquidity threshold for movers.
- New releases/reminders.
- Pre-release digital binder.
- Quick Add + batch intake + continuous scanning.
- Notification categories + Action Required.
- In-app/push/email preferences.
- Optional digests.
- Saved searches + Recently Viewed.
- Wishlist separate from Watchlist.
- Favourite assets.
- Customisable home.
- Helpful empty states.
- Responsive web + PWA first.
- Privacy-first defaults.
- Data export/account deletion.
- One account/one Vault across devices.
- Offline Card Show cache later.

## Governance

- Risk-based identity verification.
- Financial/custody functionality uses appropriate adult eligibility.
- Risk-based 2FA/step-up security.
- Cooling periods for sensitive changes.
- Internal risk signals/scoring.
- Risk-based listing review.
- Duplicate cert detection.
- Market-data trust weighting.
- User reports.
- Tiered enforcement.
- Reputation / Risk / Enforcement separate.
- Structured disputes + immutable transaction snapshots.
- No universal change-of-mind return.
- Chargeback investigation rather than automatic ban.
- Negative-balance support.
- Detect transaction off-platform circumvention.
- Dedicated ops console.
- RBAC + dual approval + append-only audit.
- Scanner-driven physical custody.
- Security notifications + active sessions.
- Scoped/rate-limited APIs.
- Security disclosure.
- Public methodology/policy transparency.
- Verification revocation preserves history.
- Legitimate anonymised sales retained after account ban/deletion.
- Blocking cannot evade transactions.

## Architecture

- Modular monolith.
- Monorepo.
- Next.js + TypeScript.
- PostgreSQL/Supabase.
- RLS-safe reads + server-side sensitive mutations.
- Logical DB domain separation.
- Opaque internal IDs + friendly non-sequential public IDs.
- Current owner + ownership ledger.
- Current custody + custody ledger.
- Explicit state machines.
- Internal double-entry-style ledger.
- Payment-provider abstraction.
- Trade Vault settlement engine.
- Canonical catalogue + provider mappings.
- Background market pipeline.
- Managed queues/cron first.
- Postgres search first; dedicated search later.
- Separate media security classes.
- Server-side AI gateway.
- Store AI prediction + confirmed result.
- Domain events + transactional outbox.
- Central notification service.
- Append-oriented critical records.
- Separate ops app.
- Dev/Staging/Production.
- Version-controlled migrations.
- Unit/Integration/E2E/RLS/idempotency/concurrency tests.
- Internal API boundaries now; public API later.
- Hybrid data deletion/retention.
- Design all domains; implement only current phase.
- Deliberately scalable foundation.

## Visual design

- Obsidian Mint default.
- Background `#0B0F14`.
- Surface `#141B22`.
- Glass `#1C2733`.
- Vault Mint `#2EE6C5`.
- Signal Blue `#66A8FF`.
- Frosted Mint `#A7F3E8`.
- Dark, premium, collector-first.
- Restrained Liquid Glass.
- Smooth motion.
- Card art provides most screen colour.
- Semantic design tokens support future themes.
