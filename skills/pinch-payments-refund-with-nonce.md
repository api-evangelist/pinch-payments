---
name: Issue an idempotent refund
description: Safely refund a payment using a nonce to prevent duplicate refunds, then track its status.
api: openapi/pinch-payments-core.yml
operations: [check-refund-nonce, create-a-refund, get-refund]
auth: OAuth2 client-credentials (Bearer)
---

# Issue an idempotent refund with Pinch

Refund a payment (full or partial) without risk of double-refunding on retry.

## Prerequisites
- OAuth Bearer token (scope=api1); `pinch-version: 2020.1`; base URL `/test/` or `/live/`.
- A payment id (`pmt_...`) that has been approved/settled.

## Steps
1. **(Optional) Check the nonce** — `check-refund-nonce` (`POST /refunds/nonce`) with your chosen `nonce`. If `isNonceReplay` is `true`, a refund with that nonce already exists — reuse the returned `data` instead of creating another.
2. **Create the refund** — `create-a-refund` (`POST /refunds`) with `paymentId`, `amount` (cents), `reason`, and a unique `nonce`. Returns `ref_...` with status `requested`.
3. **Track status** — `get-refund` (`GET /refunds/{id}`) to follow it through `requested → pending-return → pending-clearance → processing → completed` (or `failed` / `cancelled-declined`).

## Rules
- **Idempotency:** always send a stable unique `nonce`. If you retry, Pinch detects the replay (HTTP 403 with `isNonceReplay=true` and the original refund under `data`) rather than issuing a second refund.
- Refunds can only be issued against payments that reached an approved/settled state; a refund before settlement returns the payment `returned-without-settlement`.
- Refund progress emits `refund-created` / `refund-updated` webhook events.
