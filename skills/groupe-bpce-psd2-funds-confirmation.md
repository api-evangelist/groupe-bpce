---
name: groupe-bpce-psd2-funds-confirmation
description: Check funds availability (CBPII) using the Groupe BPCE API STORE contracts.
api: openapi/groupe-bpce-psd2-funds-availability-openapi.yml
operations:
- fundsConfirmationsPost
generated: '2026-10-09'
method: generated
source: openapi/groupe-bpce-psd2-funds-availability-openapi.yml
---

# Check funds availability (CBPII)

1. Obtain a token for the PSU (`accessCode`) or client (`clientCredentials`) as declared in the contract.
2. Call `fundsConfirmationsPost` with the account and instructed amount; read the boolean funds-availability result.

## Rules

- Every operation is grounded in an operationId present in `openapi/groupe-bpce-psd2-funds-availability-openapi.yml`.
- Production calls go to the per-bank `oba-bad-me-live-api` hosts; the contract lists a sandbox server where one exists.
- Send the `X-Request-ID`/correlation headers the contract declares and handle 401/403/429 responses as declared; retries of POSTs are not documented as idempotent.
