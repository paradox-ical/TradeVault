# Trade Vault — Security, Risk & Governance Model

## 1. Principle

> **Protection scales with risk.**

Ordinary collection use remains low friction. Higher-value or higher-risk actions progressively add stronger controls.

## 2. Identity verification

Full legal identity is not required for ordinary private collection tracking.

Identity verification becomes required where appropriate for:
- selling;
- payouts;
- high-value buying;
- high-value trading;
- verification;
- grading;
- Vault use;
- dealer onboarding.

Public identity remains username-based.

## 3. Age controls

Collection/community may support eligible younger users. Financial, contractual and custody services require appropriate Australian legal/payment-provider rules and formal legal review.

## 4. Authentication

Encourage strong authentication for everyone.

Require stronger authentication for higher-risk roles/actions, including sellers, dealers, Vault users, payout changes, withdrawals and high-value transactions.

Passkeys preferred long-term.

## 5. Step-up authentication

Sensitive changes may require reauthentication/2FA/passkey:
- email;
- password/passkey;
- 2FA;
- payout details;
- Vault withdrawal address;
- high-value withdrawal.

Risky changes may create cooling periods.

## 6. Privacy defaults

Default:
- collection private;
- financial totals private;
- acquisition cost private;
- exact location private;
- local discovery off;
- DMs restricted;
- Vault holdings/count hidden.

Private data must be inaccessible through public APIs, not merely hidden in components.

## 7. RLS / authorisation tests

Required tests include:
- User A cannot read User B's private Vault.
- User A cannot mutate User B's assets.
- Dealer staff cannot see finance-only data without permission.
- Public profile projection does not expose private cost basis.
- Blocking does not interrupt existing transactional obligations.

## 8. Risk engine

Store individual explainable signals such as:
- DUPLICATE_CERT
- REUSED_IMAGES
- NEW_DEVICE_HIGH_VALUE
- CHARGEBACK_HISTORY
- CONNECTED_BANNED_ACCOUNT
- SUSPICIOUS_TRANSACTION_VELOCITY
- MARKET_MANIPULATION_PATTERN
- PAYOUT_DETAILS_CHANGED

A derived internal risk level can trigger controls. Never expose a raw suspicion score publicly.

## 9. Listing risk

Flag cert mismatch, duplicate cert, reused images, impossible variant/grade, suspicious pricing, counterfeit indicators and unsupported inventory.

Higher-risk listings can become `UNDER_REVIEW`.

## 10. Market manipulation

First-party sales do not automatically receive full pricing weight.

Exclude/down-weight related accounts, self-dealing, refunded transactions, suspicious counterparties, unpaid transactions and manipulation patterns.

## 11. Reports

Users can report users, listings, messages, posts, reviews and verification records.

Reasons include counterfeit, scam, incorrect listing, stolen images, harassment, spam, prohibited content, price manipulation, suspicious account and other.

## 12. Enforcement

Potential actions:
- warning;
- content removal;
- messaging restriction;
- marketplace restriction;
- trading restriction;
- payout hold;
- temporary suspension;
- permanent ban.

Fraud can skip progressive stages.

Reputation, risk and enforcement remain separate.

## 13. Disputes

Structured cases preserve immutable listing snapshot, images, condition, messages, tracking, payment data, verification and proposal history.

Payout pauses when policy requires.

## 14. Returns

No universal change-of-mind requirement for ordinary collector listings.

Protection returns may apply to counterfeit, wrong item, material mismatch, undisclosed damage and other covered cases.

## 15. Off-platform circumvention

Detect attempts to move active marketplace transactions to external payment methods.

Possible response: warning, blocked content, transaction warning and repeated-offence restriction.

## 16. Prohibited inventory

At minimum:
- counterfeit cards;
- fake slabs;
- misrepresented proxies;
- stolen items;
- mystery listings used to avoid identification;
- unsupported prohibited categories.

## 17. Counterfeit physical submissions

Formal legal policy required.

Software supports verification failure, evidence preservation, risk signal, transaction freeze, quarantine and escalation.

Do not improvise physical disposition in code.

## 18. Staff RBAC

Roles:
- Support
- Moderator
- Risk
- Verification
- Vault
- Finance
- Catalogue/Data
- Super Admin

Least privilege.

## 19. Dual approval

Two authorised staff for defined high-risk manual operations such as high-value ownership override, withdrawal override, custody correction, exceptional refund and verification revocation.

Initiator cannot approve own request.

## 20. Audit

Sensitive staff action records actor, timestamp, target, before state, after state, reason and case/reference. Audit history is append-oriented.

## 21. Physical custody

Physical movement should be scanner-driven where practical.

Location mismatch creates a discrepancy workflow. Missing asset creates a high-priority exception and commercial lock.

## 22. Finance security

Provider balance is not accounting truth.

Use internal ledger + automated reconciliation.

Critical finance operations require idempotency, immutable entries, webhook verification, replay safety, settlement holds and reconciliation alerts.

## 23. Production database access

Ordinary support/admin staff do not receive direct production DB credentials.

Exceptional access is authorised and auditable.

## 24. Disaster recovery

Architect automated backups, point-in-time recovery, redundant/off-site backup, media redundancy, monitoring, incident response and recovery testing.

Physical operations require separate business continuity planning.

## 25. Security disclosure

Launch with a responsible security disclosure process. Formal bug bounty can follow later.

## 26. Transparency

Publish understandable versions of fees, buyer protection, seller requirements, verification methodology overview, condition standards, pricing methodology, privacy, moderation and relevant conflicts/affiliate disclosures.

Do not publish exploitable anti-fraud details.
