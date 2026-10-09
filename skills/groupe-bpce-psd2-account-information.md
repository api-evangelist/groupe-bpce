---
name: groupe-bpce-psd2-account-information
description: Retrieve PSD2 account information (AISP) using the Groupe BPCE API STORE contracts.
api: openapi/groupe-bpce-psd2-accounts-openapi.yml
operations:
- accountsGet
- consentsPut
- accountsBalancesGet
- accountsTransactionsGet
- accountsTransactionsDetailsGet
generated: '2026-10-09'
method: generated
source: openapi/groupe-bpce-psd2-accounts-openapi.yml
---

# Retrieve PSD2 account information (AISP)

1. Obtain a PSU access token through the STET OAuth2 authorization code flow (`accessCode` scheme) as an eIDAS-certified AISP.
2. Call `accountsGet` to list the PSU accounts and their `accountResourceId`s.
3. If balances/transactions are not yet authorised, call `consentsPut` to forward the PSU consent for those accounts.
4. Call `accountsBalancesGet` and `accountsTransactionsGet` for each account; use `accountsTransactionsDetailsGet` for a single transaction.

## Rules

- Every operation is grounded in an operationId present in `openapi/groupe-bpce-psd2-accounts-openapi.yml`.
- Production calls go to the per-bank `oba-bad-me-live-api` hosts; the contract lists a sandbox server where one exists.
- Send the `X-Request-ID`/correlation headers the contract declares and handle 401/403/429 responses as declared; retries of POSTs are not documented as idempotent.
