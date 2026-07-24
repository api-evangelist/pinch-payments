---
name: Set up a direct debit and reconcile settlement
description: Create a payer and bank source, schedule a direct-debit payment, then reconcile the settlement transfer.
api: openapi/pinch-payments-payments.yml
operations: [save-payer, create-payment-source, save-payment, list-all-transfers, list-transfer-line-items]
auth: OAuth2 client-credentials (Bearer)
---

# Direct debit and reconcile with Pinch

Collect a bank-account (BSB + account) direct-debit payment and match the settled funds back to your records.

## Prerequisites
- OAuth Bearer token (scope=api1); `pinch-version: 2020.1`; base URL `/test/` or `/live/`.

## Steps
1. **Create the payer** — `save-payer` (`POST /payers`). Returns `pyr_...`.
2. **Attach a bank source.** Tokenise the bank account client-side with CaptureJS (`sourceType:"bank-account"`, bankAccountName/Routing/Number) to get a `tkn_...`, then `create-payment-source` (`POST /payers/{payerId}/sources`) to store it. Returns `src_...`.
3. **Schedule the payment** — `save-payment` (`POST /payments`) with `payerId`, `amount` (cents), `description`, and a `transactionDate`. Direct-debit payments process overnight and sit in `processing` for 1-3 business days.
4. **Watch for the result** via the `bank-results` webhook event (dishonour codes on failure). See asyncapi/pinch-payments-webhooks.yml.
5. **Reconcile settlement** — `list-all-transfers` (`GET /transfers`) to find the settlement batch, then `list-transfer-line-items` (`GET /transfers/{id}/line-items`) to map each transferred amount back to the underlying `pmt_...` payments.

## Rules
- **Idempotency:** include a unique `nonce` on the payment to avoid double debits.
- **Failure handling:** on `insufficient-funds` wait ≥24h then retry with a new `transactionDate`; pause after 3 consecutive failures. See errors/pinch-payments-decline-codes.yml.
- **Testing:** use test bank accounts (BSB `000-000`, account `0000000000`) and the `Time-Travel` header to fast-forward overnight processing and settlement. See sandbox/pinch-payments-sandbox.yml.
