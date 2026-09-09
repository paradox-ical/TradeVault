# Trade Vault — Master Product Blueprint

**Primary market:** Australia  
**Architecture:** Global-ready  
**Default visual identity:** Obsidian Mint

## 1. Vision

> **The collection is the platform.**

Trade Vault is an all-in-one trading-card ecosystem where a physical collectible enters the system once and can then be:

**Discovered → Collected → Tracked → Valued → Showcased → Traded → Sold → Graded → Verified → Vaulted**

The same persistent asset can accumulate ownership, acquisition and cost basis, images, condition observations, grading certifications, market estimates, listings/offers, trade history, verification reports, custody history and provenance.

Positioning:

> **Your collection. Your market. Your trades. Your vault.**

## 2. Initial TCG scope

Launch target support:
- Pokémon
- Magic: The Gathering
- Yu-Gi-Oh!
- One Piece Card Game
- Disney Lorcana
- Riftbound

Architecture remains TCG-agnostic.

## 3. Catalogue model

Trade Vault owns canonical catalogue identity.

```text
catalogue.item
├── card_printing
└── sealed_product
```

Optional conceptual card relationships support search/discovery across related printings and languages.

External provider IDs are mappings only.

## 4. Asset model

> **One physical collectible = one asset record.**

Four copies create four assets even if UI displays `×4`.

Digital My Vault supports raw singles, graded singles and sealed products.

Physical custody initially focuses on raw and graded singles.

## 5. My Vault

Default experience: hybrid collection + portfolio dashboard.

Views:
- Binder
- Grid
- List

Organisation:
- Binders
- Tags
- Favourites
- Set completion
- Saved views/filters
- Private owner storage locations

Private storage locations are never public.

## 6. Adding collectibles

Detailed-first but compact.

Methods:
- manual search;
- Quick Add;
- continuous camera scan;
- image upload;
- barcode scan;
- batch intake;
- CSV import;
- compatible migration/import.

AI may suggest TCG, card, set, number, language, variant, raw/graded, grader, grade and certification. User confirms.

## 7. Raw condition

Initial scale:
- Mint
- Near Mint
- Excellent
- Good
- Poor

Raw condition does not automatically generate separate headline portfolio pricing at launch.

Owner and Trade Vault condition observations remain separate historical facts.

## 8. Photography

Private collection records do not require images.

Owner-held raw sale/trade publication requires actual front + back photos.

Images live on the asset, not just the listing.

## 9. Portfolio and pricing

Portfolio may show:
- total value;
- cost basis;
- unrealised/realised gain/loss;
- historical value;
- breakdown by TCG/set;
- raw vs graded;
- largest holdings/movers.

Headline card pricing includes:
- Trade Vault market estimate;
- last sale;
- recent average;
- lowest active listing;
- confidence.

Pricing supports **Australia | Global**.

Completed sales carry greater weight than active asks.

## 10. Price transparency

Price evidence is inspectable.

Trade Vault always distinguishes:
- `SOLD`
- `ACTIVE ASKING PRICE`

Potential outliers may be excluded but remain inspectable.

Confidence:
- High
- Medium
- Low

Users may also keep a private personal valuation.

## 11. Wishlist and Watchlist

### Wishlist

“I want to own this.”

Can include exact printing, raw/graded, grader, minimum grade, maximum price and trade preference.

Used strongly by Trade Finder.

### Watchlist

“I want to monitor this market.”

Used for price/listing alerts.

## 12. Marketplace

Launch listing types:
- Fixed Price
- Fixed Price + Offers
- Trade Only
- Sale or Trade

Auctions deferred.

Listings should originate from owned assets whenever possible. Marketplace-first listing creates the underlying asset.

## 13. Listing flow

Existing asset information is reused.

Seller primarily chooses:
- price;
- offers;
- trade status;
- shipping;
- shipping cost;
- notes.

Trade Vault provides contextual pricing assistance but does not dictate price.

## 14. Offers

Launch:
- Offer
- Accept
- Decline
- Counteroffer

Negotiation uses immutable revisions and configurable expiration.

Long-term, an offer may include explicit purchase authorisation if accepted.

## 15. Marketplace payments

Trade Vault handles buyer payment, fees, order, refunds, disputes, seller settlement and buyer protection.

**Payment, order, fulfilment, ownership and seller settlement are separate concepts.**

## 16. Buyer protection

May cover:
- non-delivery;
- wrong item;
- counterfeit;
- material undisclosed damage;
- grade/cert mismatch;
- material listing discrepancy.

Normally excludes:
- buyer remorse;
- change of mind;
- market movement;
- accurately represented subjective dissatisfaction.

## 17. Shipping

Supports:
- Trade Vault integrated shipping;
- seller-managed supported tracking.

Risk controls scale with transaction value.

High-value transactions may automatically route through Trade Vault Verification.

## 18. Local pickup

Local transactions remain in Trade Vault. Both sides confirm handoff. Exact addresses are never public.

## 19. Marketplace fees

Working strategic target:
- approx. 2% buyer;
- approx. 2% seller;
- no ordinary listing fee.

Final rates require payment/tax/fraud/support modelling.

All fees are visible before commitment.

## 20. Cart

Launch: same-seller multi-item checkout.

Long-term: universal multi-seller checkout.

Parent checkout exists in the model from day one.

## 21. Trading

Asset states:
- Not for Trade
- Open to Offers
- Available for Trade

Trade proposals can contain multiple assets each side plus one-direction cash adjustment and immutable revisions.

## 22. Trade Finder

Core feature using:
- wishlists;
- trade inventory;
- values;
- TCG;
- raw/graded;
- grade;
- location;
- shipping/local preference;
- cash willingness;
- verification state.

Basic matching is free; advanced matching can be Pro.

## 23. Trade fulfilment

Modes:
- Direct
- Verified
- Local
- Vault-to-Vault

Pending proposals do not hard-lock assets; conflicting activity invalidates them.

Accepted trades atomically lock every involved asset.

Direct trade ownership swaps atomically only when both sides satisfy completion rules.

## 24. Mandatory high-value verification

Direct sale/trade can be disabled when a configurable value/risk policy requires physical Trade Vault Verification.

Policy can consider individual value, total value, raw/graded, verification history, custody, reputation, fraud and category risk.

Users cannot bypass verification by changing transaction type.

## 25. Trade Vault Verification

Verification promises:
- identity;
- correct variant;
- authenticity assessment;
- documented condition/material defects.

It is **not numerical grading**.

Result:
- Pass
- Review
- Fail

Verified items receive a public friendly verification ID.

## 26. Verification and custody

Historical verification is permanent. Current custody is separate.

Example:

**Trade Vault Verified — 4 Sep 2026**  
**Owner Held**

versus:

**Trade Vault Verified — 4 Sep 2026**  
**Continuous Trade Vault Custody ✓**

The second carries stronger assurance.

## 27. Public verification lookup

Can show item, date, status/type, approved evidence, continuity and revocation. Owner identity remains private.

## 28. Grading hub

Long-term:
- Verify Only
- PSA
- BGS
- CGC
- other supported graders

Trade Vault may manage intake, imaging, paperwork, shipping, status, result, return and optional Vault storage.

Raw → graded remains the same physical asset ID.

## 29. Pre-grading

Potential AI screening plus optional human assessment. Estimates are not official grades and cannot guarantee outcome.

## 30. Physical Vault

Initially raw + graded singles.

Potential services:
- secure storage;
- insurance;
- imaging;
- verification;
- grading submission;
- marketplace fulfilment;
- trading;
- digital ownership transfer;
- withdrawal.

Vault-to-Vault sale/trade can change owner without moving the card.

## 31. Custody invariant

> **If Trade Vault claims physical custody of an asset, the system must identify the responsible custodian and latest reconciled physical location or active transit workflow.**

Operational location is never public.

## 32. Community

Tabs:
- For You
- Following
- TCGs
- Showcases

Content focuses on pickups, grading, completed sets, trades, binders, showcases, Vault milestones and limited general TCG posts.

Community exists to serve collecting, not generic infinite-scroll social media.

## 33. Profiles

May include username, avatar, bio, favourite TCGs, interests, showcase, public binders, wishlist, followers/following, seller/trader reputation, trust badges and achievements.

Financial collection totals are private by default.

## 34. Interactions

- Follows
- Privacy-controlled DMs
- Comments
- ❤️ Love It
- 🔥 Heat
- 🤝 Trade?
- 🏆 Grail

When eligible, Trade? can launch proposal flow.

## 35. Card Show Mode

Temporary event mode emphasises QR, trade inventory, wishlist, local availability and showcase. Limited offline cache is desirable later.

## 36. Dealer accounts

Dedicated organisation accounts with future business verification, storefront, branding, staff access, bulk inventory/listing, feeds, analytics, commercial fees and APIs.

## 37. Free / Pro / Dealer

### Free

Unlimited basic collection, basic portfolio, current/recent pricing, marketplace, trading, community, basic Trade Finder, imports, limited AI, limited alerts, wishlist/watchlist.

### Pro

Target positioning A$10–15/month subject to modelling.

Adds deeper history, advanced analytics, larger AI/alerts, advanced Trade Finder, lower marketplace/verification fees, small Vault allowance, exports and customisation.

Subscription is not a trust badge.

### Dealer

Higher recurring fee plus lower commercial rates and B2B tools.

## 38. Monetisation principle

> **Make collecting excellent for free. Monetise advanced capability, transactions and real services.**

Potential revenue includes marketplace, Pro, Dealer, verification, grading handling, Vault storage, withdrawal, fulfilment, imaging, promoted listings, disclosed relevant partnerships and professional data/API.

## 39. Guest and onboarding

Guests can browse catalogue, pricing, public marketplace and public profiles/showcases.

Signup:
- email;
- Apple;
- Google;
- passkeys later.

Short onboarding:
1. username;
2. country/currency;
3. favourite TCGs;
4. collector interests;
5. optional region;
6. optional collection size.

Then choose Add Cards, Import Collection, Explore Market or Browse Marketplace.

## 40. Search and Explore

Universal fuzzy search spans cards/products, sets, listings, profiles and public binders/showcases. Exact matches beat personalisation.

Explore includes trending, movers, new releases, popular sets, most wishlisted, grading trends and market discovery.

Trending uses a composite score, not price movement alone.

## 41. Notifications

Categories:
- Market
- Trades
- Orders
- Community
- Grading
- Vault

Critical operational notifications live in **Action Required**.

Channels: in-app, push, email. Optional digest for non-critical activity.

## 42. Privacy defaults

- collection private;
- value private;
- acquisition price private;
- exact location private;
- local discovery off;
- DMs restricted;
- Vault counts hidden;
- Showcase unpublished until chosen.

## 43. Progressive trust

Basic collecting is low friction. Higher-value/risk actions progressively add identity verification, 2FA/passkeys, risk review, shipping controls, physical verification, custody controls and internal dual approval.

## 44. Governance

Separate reputation, internal risk and enforcement.

Supports reports, disputes, immutable transaction snapshots, moderation restrictions, RBAC, dual approval, audit logs and responsible security disclosure.

## 45. Visual identity

Default theme: **Obsidian Mint**.

Dark, premium, collector-first, restrained Liquid Glass, smooth microinteractions, card artwork as the main colour source.

See `docs/design/visual-design-system.md`.
