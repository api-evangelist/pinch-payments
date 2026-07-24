---
name: Create a plan and subscribe a payer
description: Define a plan of fixed + recurring payments, preview the schedule, subscribe a payer, and cancel cleanly.
api: openapi/pinch-payments-core.yml
operations: [save-plan, get_plans-planid-calculated-payments, create-subscription, get-subscription, cancel-subscription]
auth: OAuth2 client-credentials (Bearer)
---

# Plans and subscriptions with Pinch

Set up recurring billing: a Plan is a reusable template of fixed and/or recurring payments; a Subscription enrols one payer on a plan.

## Prerequisites
- OAuth Bearer token (scope=api1); `pinch-version: 2020.1`; base URL `/test/` or `/live/`.
- An existing payer (`pyr_...`) with a usable payment source.

## Steps
1. **Create the plan** — `save-plan` (`POST /plans`) with the fixed and recurring payment structure (amounts in cents or percentages). Returns `pln_...`.
2. **Preview the schedule** (optional) — `get_plans-planid-calculated-payments` (`GET /plans/{planId}/calculated-payments`) with `startDate` and (for percentage plans) `totalAmount` to see the concrete dated payments before committing.
3. **Subscribe the payer** — `create-subscription` (`POST /subscriptions`) with `planId`, `payerId`, optional `totalAmount` (cents, required for percentage plans), `startDate`, and `surcharge`. Returns `sub_...` with status `active`.
4. **Check status** — `get-subscription` (`GET /subscriptions/{id}`).
5. **Cancel** — `cancel-subscription` (`DELETE /subscriptions/{id}`) to stop future payments.

## Rules
- Percentage-based plans require `totalAmount` on the subscription; it overrides recurring end settings.
- `surcharge` values are `bank-account` and/or `credit-card` to pass fees to the payer.
- Subscription lifecycle emits `subscription-created` / `subscription-cancelled` / `subscription-complete` webhook events. See asyncapi/pinch-payments-webhooks.yml.
