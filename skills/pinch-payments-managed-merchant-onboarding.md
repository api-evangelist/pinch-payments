---
name: Onboard a managed (sub-) merchant
description: Create a sub-merchant under your own credentials, submit financial data and compliance documents, then list managed merchants.
api: openapi/pinch-payments-merchants.yml
operations: [create-managed-merchant, saveMerchantFinancialData, upload-document, list-managed-merchants]
auth: OAuth2 client-credentials (Bearer)
---

# Onboard a managed merchant (Payfac-as-a-Service) with Pinch

Platforms and marketplaces use Managed Merchants ("Glassbox") to create and control Pinch merchant accounts under their own credentials.

## Prerequisites
- OAuth Bearer token (scope=api1) for your platform application; `pinch-version: 2020.1`; base URL `/test/` or `/live/`.

## Steps
1. **Create the sub-merchant** — `create-managed-merchant` (`POST /merchants`) with the business/contact details. Returns `mch_...`.
2. **Submit financial data** — `saveMerchantFinancialData` (create/update merchant financial data used in compliance/onboarding). Retrieve later with `getCurrentMerchantFinancialData`.
3. **Upload compliance documents** — `upload-document` (multipart) for the KYC documentation Pinch requires before settlements are enabled. See the Compliance guide (https://docs.getpinch.com.au/docs/compliance-process).
4. **Track and list** — `list-managed-merchants` (`GET /merchants`) to see your portfolio; watch the `compliance-updated` and `merchant-updated` webhook events for status changes.

## Rules
- Until compliance checks pass, payments may clear with settlement disabled (`cleared-settlements-disabled` payment status). See payment statuses in errors/conventions.
- Take payments on the sub-merchant's behalf using the standard payment operations once onboarded. See skills/pinch-payments-take-card-payment.md.
- `upload-document` is a `write`/physical-consequence operation in the agentic-access model — require human review before automating. See agentic-access/pinch-payments-agentic-access.yml.
