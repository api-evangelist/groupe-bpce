---
name: groupe-bpce-open-finance-transfer
description: Move money between accounts (Open Finance Transfer) using the Groupe BPCE API STORE contracts.
api: openapi/groupe-bpce-open-finance-transfer-openapi.yml
operations:
- getInternalAccounts
- getExternalAccounts
- createExternalAccount
- createTransferRequest
- createTransferRequestTransferRequestLine
- createTransferRequestConfirmation
- getTransferRequest
- getTransferRequestErrors
generated: '2026-10-09'
method: generated
source: openapi/groupe-bpce-open-finance-transfer-openapi.yml
---

# Move money between accounts (Open Finance Transfer)

1. Authenticate with OAuth2 authorization code + PKCE (`oauth2-authorizationCodePKCE-moneyTransfer`).
2. List debit sources with `getInternalAccounts` and beneficiaries with `getExternalAccounts`; add a beneficiary with `createExternalAccount`.
3. Create a transfer with `createTransferRequest`, add lines with `createTransferRequestTransferRequestLine`.
4. Confirm with `createTransferRequestConfirmation`, then check `getTransferRequest` and `getTransferRequestErrors`.

## Rules

- Every operation is grounded in an operationId present in `openapi/groupe-bpce-open-finance-transfer-openapi.yml`.
- Production calls go to the per-bank `oba-bad-me-live-api` hosts; the contract lists a sandbox server where one exists.
- Send the `X-Request-ID`/correlation headers the contract declares and handle 401/403/429 responses as declared; retries of POSTs are not documented as idempotent.
