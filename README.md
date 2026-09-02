# BLMPay OpenAPI

Official OpenAPI 3.1 specification for the BLMPay API v1.

This repository is the public source of truth for BLMPay developer-facing endpoints, authentication, request/response schemas, webhooks, payment flows, payout flows, payment links, invoices and USDT APIs.

## Specification

- `blmpay-v1.yaml` — BLMPay API v1 OpenAPI 3.1 document.
- Base URL: `https://pay.blmtec.co.tz/api/v1`
- Authentication: `Authorization: Bearer <BLMPay_API_KEY>`.

## Domain-bound API keys

BLMPay API keys may be restricted to an HTTPS integration domain. Browser requests can be identified through `Origin`/`Referer`. Server-to-server integrations using a domain-bound key must send:

```http
X-BLMPay-Origin: https://example.com
```

The host must match the integration domain saved on that API key. A mismatch may return `403 integration_domain_not_allowed`; a restricted key without an identifiable origin may return `403 integration_origin_required`.

Existing legacy API keys without a saved domain remain backward compatible.

## Security

Never commit live API keys, webhook secrets or merchant credentials to source control. Do not embed privileged merchant API keys in public browser bundles, APKs or IPAs. Keep privileged credentials on a secured backend and use idempotency keys for payment/payout creation.

SDKs:
- PHP: https://github.com/Winnie7676/blmpay-sdk-php
- Node.js: https://github.com/Winnie7676/blmpay-sdk-node
- Dart/Flutter: https://github.com/Winnie7676/blmpay-sdk-flutter
- MCP: https://github.com/Winnie7676/blmpay-mcp

Powered by BLMSoft.
