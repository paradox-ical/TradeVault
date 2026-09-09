# Trade Vault — State Machines

State machines are domain-owned. Do not invent transitions ad hoc in UI code.

## 1. Listing

```text
DRAFT
→ ACTIVE
   → RESERVED
      → SOLD
      → ACTIVE        (reservation expiry)
   → CANCELLED
   → EXPIRED
   → UNDER_REVIEW
   → SUSPENDED
```

Reserved/paid listings cannot be casually cancelled.

## 2. Payment

```text
REQUIRES_PAYMENT
→ PROCESSING
   → SUCCEEDED
   → FAILED
   → CANCELLED
```

Post-success dimensions may include partially refunded, refunded and disputed.

Payment state is not order state.

## 3. Order

Use separate dimensions.

### Commercial

```text
DRAFT
→ PAYMENT_PENDING
→ ACTIVE
→ COMPLETED
```

Branch: CANCELLED.

### Fulfilment

```text
NOT_STARTED
→ FULFILMENT_PENDING
→ SHIPPED / IN_VERIFICATION / VAULT_TRANSFER
→ DELIVERED
→ INSPECTION
→ COMPLETE
```

### Dispute

```text
NONE → OPEN → RESOLVED
```

### Settlement

```text
NOT_PAYABLE → PAYABLE → PAYOUT_PENDING → PAID
```

Holds are separate records.

## 4. Trade negotiation

```text
DRAFT
→ PROPOSED
→ COUNTERED
→ ACCEPTED
```

Branches:
- REJECTED
- INVALIDATED

Each sent/counter version is immutable.

## 5. Trade fulfilment

Direct:

```text
NOT_STARTED
→ AWAITING_SHIPMENT
→ IN_TRANSIT
→ DELIVERED
→ READY_FOR_COMPLETION
→ COMPLETE
```

Verified:

```text
AWAITING_SHIPMENT
→ TRADE_VAULT_INTAKE
→ UNDER_VERIFICATION
→ READY_FOR_EXCHANGE
→ OUTBOUND / VAULT_TRANSFER
→ COMPLETE
```

Exception: `FULFILMENT_EXCEPTION`.

Do not automatically fail once physical property has moved.

Direct trade ownership swaps atomically only when both required legs satisfy completion criteria.

## 6. Verification case

```text
AWAITING_ITEM
→ ITEM_RECEIVED
→ ASSIGNED
→ UNDER_REVIEW
→ COMPLETED
```

Result:
- PASS
- REVIEW
- FAIL

Report may later be REVOKED/SUPERSEDED.

## 7. Inbound item

```text
EXPECTED
→ RECEIVED
→ RECONCILED
→ INTAKE_COMPLETE
```

Branches:
- UNEXPECTED
- MISMATCHED
- DAMAGED_IN_TRANSIT
- MISSING
- RECONCILIATION_REQUIRED

## 8. Vault admission

```text
VERIFICATION_PASSED
→ VAULT_ADMISSION_APPROVED
→ LOCATION_ASSIGNED
→ VAULT_HELD
```

Verification pass does not mean storage completed.

## 9. Custody

```text
OWNER_HELD
→ INBOUND_TO_TRADE_VAULT
→ TRADE_VAULT_HELD
→ OUTBOUND_FROM_TRADE_VAULT
→ OWNER_HELD
```

Third-party custody can include carrier/PSA/BGS/CGC/approved custodian.

## 10. Withdrawal

```text
REQUESTED
→ SECURITY_REVIEW
→ APPROVED
→ PICKING
→ PACKING
→ DISPATCHED
→ DELIVERED
→ COMPLETE
```

Branches:
- CANCELLED
- ON_HOLD
- EXCEPTION

`not_before` can enforce cooling periods.

## 11. Enforcement

Append-oriented actions include warning, marketplace restriction, trading restriction, payout hold, suspension, ban and restriction lifted.

Do not reduce enforcement history to `is_banned`.

## 12. Transition rule

Every critical transition must:
1. validate current state;
2. validate actor authority;
3. validate linked invariants;
4. apply atomically where necessary;
5. increment version;
6. write history;
7. write outbox event where meaningful;
8. be idempotent where retries are possible.
