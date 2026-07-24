# Pinch Payments (pinch-payments)

Pinch Payments is an Australian, Brisbane-based payment orchestration and payment-facilitator platform that automates invoice collection and receivables for service businesses, bookkeepers, and software platforms across Australia and New Zealand. It lets merchants accept direct debit (bank account) and card payments (Visa, Mastercard, American Express), build payment plans and subscriptions, tokenise payment sources client-side with CaptureJS, and reconcile settlements into Xero, QuickBooks, and MYOB. Its Glassbox / Managed Merchants product is a Payfac-as-a-Service seam with KYC, compliance, and sub-merchant onboarding for platforms and marketplaces.

Pinch is genuinely API-first: a fully documented REST API (JSON, OAuth2 client-credentials auth), a ReadMe-hosted developer portal with a live explorer, per-product OpenAPI 3.1 definitions, a published Postman collection, an official .NET SDK, Zapier/n8n/viaSocket connectors, webhooks, and an llms.txt + docs MCP server for AI-assisted integration.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/pinch-payments/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/pinch-payments/refs/heads/main/apis.yml)

## Tags

- Payments
- Australia
- Payment Gateway
- Payment Processing
- Direct Debit
- Card Payments
- Subscriptions
- Billing
- Payment Facilitator
- Account-to-Account
- New Zealand

## Timestamps

- **Created:** 2026-07-24
- **Modified:** 2026-07-24

## APIs

### Pinch Core API

Core Pinch REST API covering scheduled and realtime payments, plans and subscriptions, refunds, fees, events, and health (14 paths / 19 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/things-to-know](https://docs.getpinch.com.au/reference/things-to-know)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-core.yml)
- [Documentation](https://docs.getpinch.com.au/docs/pinch-payments-api-core-concepts)

### Pinch Payments API

Create/update scheduled payments, take realtime card payments, retrieve/list payments, check payment nonces, delete payments (7 paths / 8 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/save-payment](https://docs.getpinch.com.au/reference/save-payment)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-payments.yml)
- [Documentation](https://docs.getpinch.com.au/docs/credit-card-payments)

### Pinch Payers API

Manage payer records and payment sources (bank account or credit card) plus client-side tokenisation (4 paths / 6 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/save-payer](https://docs.getpinch.com.au/reference/save-payer)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-payers.yml)

### Pinch Payment Links API

Generate hosted payment pages and share them via email, SMS, or chat with no frontend work (3 paths / 5 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/create-payment-link](https://docs.getpinch.com.au/reference/create-payment-link)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-payment-links.yml)
- [Documentation](https://docs.getpinch.com.au/docs/payment-links)

### Pinch Merchants API

Payfac-as-a-Service / Managed Merchants — create sub-merchant accounts, update merchant details, list managed merchants, upload compliance documents (3 paths / 4 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/create-managed-merchant](https://docs.getpinch.com.au/reference/create-managed-merchant)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-merchants.yml)
- [Documentation](https://docs.getpinch.com.au/docs/managed-merchants)

### Pinch Webhooks API

Configure webhooks for real-time event notifications; create/update, list, retrieve, delete webhooks (2 paths / 4 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/create-or-update-webhook](https://docs.getpinch.com.au/reference/create-or-update-webhook)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-webhooks.yml)
- [Documentation](https://docs.getpinch.com.au/docs/webhooks)

### Pinch Contacts API

Manage contact records for the authenticated merchant (2 paths / 4 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/save-contact](https://docs.getpinch.com.au/reference/save-contact)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-contacts.yml)

### Pinch Transfers API

Reconcile settlements — list transfers, retrieve a transfer, list its line items back to payments (3 paths / 3 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/list-all-transfers](https://docs.getpinch.com.au/reference/list-all-transfers)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-transfers.yml)
- [Documentation](https://docs.getpinch.com.au/docs/transfers-in-pinch-payments)

### Pinch Merchant Financial Data API

Retrieve and save merchant financial data used in compliance and onboarding (2 paths / 2 operations).

- **Human URL:** [https://docs.getpinch.com.au/reference/getcurrentmerchantfinancialdata](https://docs.getpinch.com.au/reference/getcurrentmerchantfinancialdata)
- **Base URL:** `https://api.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-merchant-financial-data.yml)

### Pinch Authentication API

OAuth2 client-credentials token endpoint — POST /connect/token with HTTP Basic (merchant ID + secret key) and scope `api1` to obtain a short-lived Bearer JWT.

- **Human URL:** [https://docs.getpinch.com.au/reference/tokens](https://docs.getpinch.com.au/reference/tokens)
- **Base URL:** `https://auth.getpinch.com.au`
- [OpenAPI](openapi/pinch-payments-authentication.yml)
- [Documentation](https://docs.getpinch.com.au/docs/application-authentication)

## Common Properties

- [Website](https://getpinch.com.au/)
- [Developer Portal](https://docs.getpinch.com.au/)
- [Getting Started](https://docs.getpinch.com.au/docs/get-started-with-the-pinch-api)
- [GitHub Organization](https://github.com/PinchPayments)
- [Postman Collection](https://github.com/PinchPayments/postman-pinch-api)
- [Status Page](https://status.getpinch.com.au/)
- [Pricing](https://getpinch.com.au/pricing)
- [Blog](https://getpinch.com.au/blog)
- [Help Center](https://helpdesk.getpinch.com.au/)
- [Sign Up](https://app.getpinch.com.au/register)
- [Terms of Service](https://getpinch.com.au/Legal/Terms/)
- [Privacy Policy](https://getpinch.com.au/Legal/Privacy/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
