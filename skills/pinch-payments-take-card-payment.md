---
name: Take a realtime card payment
description: Charge a credit card immediately using a CaptureJS token and confirm the result.
api: openapi/pinch-payments-payments.yml
operations: [realtime-payment, get-payment]
auth: OAuth2 client-credentials (Bearer)
---

# Take a realtime card payment with Pinch

Charge a card immediately and get a synchronous approve/decline. All amounts are integers in cents (AUD/NZD).

## Prerequisites
- An OAuth Bearer token from `POST https://auth.getpinch.com.au/connect/token` (grant_type=client_credentials, scope=api1). Cache it — it lasts 3600s.
- Send `pinch-version: 2020.1` on every request.
- Base URL: `https://api.getpinch.com.au/test/` (test) or `/live/` (production).

## Steps
1. **Tokenise the card client-side.** Use CaptureJS (`Pinch.Capture({publishableKey}).createToken({sourceType:"credit-card", ...})`) in the browser so raw card data never hits your server. You receive a short-lived `tkn_...` token. (See components/pinch-payments-components.yml.)
2. **Charge the card** — `realtime-payment` (`POST /payments/realtime`). Pass `creditCardToken` (the `tkn_...`), `amount` (cents), `description`, and payer identity fields. The response returns a payment with a `status` (e.g. `approved` or `dishonoured`) and an `id` (`pmt_...`).
3. **Confirm** — if you need to re-check later, call `get-payment` (`GET /payments/{id}`) with the returned `pmt_...` id.

## Rules
- **Failures** come back as dishonour codes (e.g. `insufficient-funds`, `invalid-card`). Do NOT retry non-retryable codes (`invalid-card`, `blocked-by-bank`, `unsupported-card`, `invalid-account`). See errors/pinch-payments-decline-codes.yml.
- **Idempotency:** pass a unique `nonce` to guard against double submission; a replay returns the original result with `isNonceReplay=true`.
- **Testing:** use test cards (e.g. `4242424242424242`, any future expiry/CVC) and force failures by putting `#<code>` in the `description`. See sandbox/pinch-payments-sandbox.yml.
