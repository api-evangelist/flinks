# Flinks (flinks)

Flinks is a Canadian financial data platform (owned by National Bank of Canada) that lets businesses connect to consumer and business bank accounts to aggregate account, transaction, and statement data, verify identity, and derive income, credit-risk, and fraud analytics. Access begins with a Flinks Connect authentication session and a multi-step /Authorize (MFA) call, after which banking, enrichment, and analytics endpoints are invoked with the returned RequestId.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/flinks/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/flinks/refs/heads/main/apis.yml)

## Tags

- Financial Data
- Open Banking
- Bank Aggregation
- Fintech
- Canada

## Timestamps

- **Created:** 2026-07-01
- **Modified:** 2026-07-01

## APIs

### Flinks Authorize / Connect API

Opens a banking session for a Flinks Connect LoginId. Handles the multi-step MFA flow - an initial /Authorize returns HTTP 203 with SecurityChallenges when a challenge is required, and a resubmission with RequestId and SecurityResponses returns HTTP 200 with the RequestId and Links used for subsequent data calls.

- **Human URL:** [https://docs.flinks.com/api/authorize/endpoints/authorize](https://docs.flinks.com/api/authorize/endpoints/authorize)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Authorize
- Connect
- MFA
- Session

#### Properties

- [Documentation](https://docs.flinks.com/api/authorize/endpoints/authorize)
- [API Reference](https://docs.flinks.com/reference/authorize)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Accounts Detail API

Returns full detail for each account linked to the session, including account identity (transit / institution / account numbers), balances, up to 90 or 365 days of transactions, and holder KYC information. Long-running requests return HTTP 202 and are polled via the /GetAccountsDetailAsync variant with the same RequestId.

- **Human URL:** [https://docs.flinks.com/reference/getaccountsdetail](https://docs.flinks.com/reference/getaccountsdetail)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Accounts
- Transactions
- Banking Data

#### Properties

- [Documentation](https://docs.flinks.com/reference/getaccountsdetail)
- [API Reference](https://docs.flinks.com/reference/step-2-calling-for-data)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Accounts Summary API

Retrieves general account information - cardholder name (when available), account balance, category, and EFT eligibility - without full transaction history, using the RequestId from /Authorize. A /GetAccountsSummaryAsync variant supports polling of long-running requests.

- **Human URL:** [https://docs.flinks.com/reference/getaccountssummary](https://docs.flinks.com/reference/getaccountssummary)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Accounts
- Balance
- Summary

#### Properties

- [Documentation](https://docs.flinks.com/reference/getaccountssummary)
- [API Reference](https://docs.flinks.com/reference/getaccountssummaryasync)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Statements API

Signs up one or more of the connected customer accounts to retrieve PDF bank statements issued by their financial institution, referenced by the session RequestId.

- **Human URL:** [https://docs.flinks.com/reference/getstatements-1](https://docs.flinks.com/reference/getstatements-1)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Statements
- PDF
- Documents

#### Properties

- [Documentation](https://docs.flinks.com/reference/getstatements-1)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Identity API

Surfaces account-holder identity captured during aggregation - name, civic address, email, and phone - and supports /FieldMatch verification that compares supplied applicant fields against the identity on the connected bank account.

- **Human URL:** [https://docs.flinks.com/reference/choose-the-correct-endpoint](https://docs.flinks.com/reference/choose-the-correct-endpoint)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Identity
- Verification
- KYC

#### Properties

- [Documentation](https://docs.flinks.com/reference/choose-the-correct-endpoint)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Attributes / Analytics API

The Enrich product returns pre-computed attribute packages derived from aggregated transaction data via /GetAttributes, plus /GetCategorization for categorized transactions and /Categories to list available transaction categories.

- **Human URL:** [https://docs.flinks.com/guides/set-up-the-attributes-api-call](https://docs.flinks.com/guides/set-up-the-attributes-api-call)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Attributes
- Enrich
- Categorization
- Analytics

#### Properties

- [Documentation](https://docs.flinks.com/guides/set-up-the-attributes-api-call)
- [API Reference](https://docs.flinks.com/docs/list-of-attributes-packages)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Score API

Analytics endpoints that summarize a connected account into decisioning signals - /GetIncomeAttributes for total, employment, and government income verification, and /GetCreditRiskAttributes for income sources, loan and bill payments, and additional risk measures.

- **Human URL:** [https://docs.flinks.com/docs/getincomeattributes-1](https://docs.flinks.com/docs/getincomeattributes-1)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Score
- Income
- Credit Risk

#### Properties

- [Documentation](https://docs.flinks.com/docs/getincomeattributes-1)
- [API Reference](https://docs.flinks.com/docs/getcreditriskattributes-1)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Flinks Fraud / KYC API

The Upload product ingests external bank statement / transaction data via /Upload and runs /FraudAnalysis to surface tampering and fraud signals, complementing the live-aggregation KYC data returned on connected accounts.

- **Human URL:** [https://docs.flinks.com/docs/legacy-api-integrations](https://docs.flinks.com/docs/legacy-api-integrations)
- **Base URL:** `https://{instance}-api.private.fin.ag/v3/{customerId}/BankingServices`

#### Tags

- Fraud
- KYC
- Upload
- Risk

#### Properties

- [Documentation](https://docs.flinks.com/docs/legacy-api-integrations)
- [OpenAPI](openapi/flinks-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/flinks.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/flinks.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/flinks)
- [Website](https://flinks.com/)
- [Documentation](https://docs.flinks.com/)
- [Plans](plans/flinks-plans-pricing.yml)
- [Rate Limits](rate-limits/flinks-rate-limits.yml)
- [Fin Ops](finops/flinks-finops.yml)

## Ownership

Flinks was acquired by **National Bank of Canada** in 2021 and operates as a wholly owned subsidiary, retaining the Flinks brand and its public HTTP REST API platform documented at [docs.flinks.com](https://docs.flinks.com/).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
