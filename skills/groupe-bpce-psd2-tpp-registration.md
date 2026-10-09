---
name: groupe-bpce-psd2-tpp-registration
description: Register a TPP client for the PSD2 APIs using the Groupe BPCE API STORE contracts.
api: openapi/groupe-bpce-psd2-registration-openapi.yml
operations:
- registrationPost
- registrationGet
- registrationPut
- registrationDelete
generated: '2026-10-09'
method: generated
source: openapi/groupe-bpce-psd2-registration-openapi.yml
---

# Register a TPP client for the PSD2 APIs

1. Register the TPP application with `registrationPost` (signed request: `Digest` and `Signature` headers are declared in the contract).
2. Read the registration back with `registrationGet` using the issued `clientId`; update it with `registrationPut`.
3. Remove it with `registrationDelete` when decommissioning.

## Rules

- Every operation is grounded in an operationId present in `openapi/groupe-bpce-psd2-registration-openapi.yml`.
- Production calls go to the per-bank `oba-bad-me-live-api` hosts; the contract lists a sandbox server where one exists.
- Send the `X-Request-ID`/correlation headers the contract declares and handle 401/403/429 responses as declared; retries of POSTs are not documented as idempotent.
