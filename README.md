# Pinch Payments (pinch-payments)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
