# Trade Vault — Domain Model

## 1. Core relationship

```text
User
  └── Membership
      └── Account
          └── owns → Asset
                       └── references → Catalogue Item
```

A user is a human identity.

An account is an ownership/commercial entity:
- Personal
- Organisation

This allows business inventory without treating a dealer as a human user.

## 2. Catalogue

```text
TCG
  ├── Set
  └── Catalogue Item
      ├── Card Printing
      └── Sealed Product
```

Optional conceptual relationships group related card printings.

External providers map into canonical Trade Vault entities.

## 3. Collection

```text
Asset
├── owner_account
├── catalogue_item
├── images
├── condition_observations
├── grading_certifications
├── cost_basis_events
├── personal_valuation_events
├── asset_events
├── ownership_events
├── binder memberships
├── tags
└── private owner storage location
```

One physical item always means one asset.

## 4. Market

```text
Catalogue Item
  └── Market Instrument
       ├── Market Observations
       ├── Market Estimates
       ├── Watchlist Entries
       └── Price Alerts
```

Market instrument can represent `item + presentation/grade + market geography`.

## 5. Commerce

```text
Asset
  └── Listing
      └── Reservation
          └── Checkout
              └── Order
                  ├── Order Item
                  │   └── Listing Snapshot
                  ├── Payment
                  ├── Fulfilment
                  ├── Dispute
                  └── Settlement
```

Payment is not ownership.

For owner-held assets, ownership transfers on successful transaction completion.

## 6. Trading

```text
Trade
├── Trade Parties
├── Trade Versions
│   ├── Version Assets
│   └── Cash Adjustment
├── Fulfilment
└── Dispute / Resolution
```

Sent proposals are immutable. Conflicting asset activity invalidates outstanding proposal versions. Acceptance atomically locks all assets. Completion atomically swaps ownership.

## 7. Verification

```text
Verification Case
  ├── Expected Identity Snapshot
  ├── Intake
  ├── Findings
  └── Verification Report
```

Reports remain historical and may be revoked/superseded without deletion.

## 8. Custody

```text
Custodian
├── Owner
├── Trade Vault
├── Carrier
└── Third-party Grader

Trade Vault Site
  └── Zone
      └── Container
          └── Slot
```

Ownership and custody are separate.

A Vault-held ownership transfer may not create a physical location event.

## 9. Finance

```text
Business Event
  └── Ledger Transaction
      ├── Ledger Entry
      └── Ledger Entry

Payment Provider Event
  ↕ reconciles with
Trade Vault Ledger
```

Seller payable and seller payout are separate.

## 10. Community

```text
Profile
├── Follows
├── Posts
│   ├── Structured Attachments
│   ├── Comments
│   └── Reactions
├── Showcase
└── Messages
```

Posts can attach to assets, catalogue items, sets, binders, grading results, trades and verification milestones.

## 11. Operations

```text
Staff User
├── Role
├── Permission
├── Audit Events
└── Approval Requests
```

Support, moderation, risk, finance, verification and Vault access use RBAC.

## 12. Never collapse these

- User vs Account
- Catalogue Item vs Physical Asset
- Current Owner vs Ownership History
- Owner vs Custodian
- Condition Claim vs Verification Observation
- Verification vs Grading
- Payment vs Order
- Order vs Fulfilment
- Fulfilment vs Ownership
- Seller Payable vs Payout
- Reputation vs Risk vs Enforcement
