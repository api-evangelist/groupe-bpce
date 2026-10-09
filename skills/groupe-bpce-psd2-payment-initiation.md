---
name: groupe-bpce-psd2-payment-initiation
description: Initiate and confirm a PSD2 payment (PISP) using the Groupe BPCE API STORE contracts.
api: openapi/groupe-bpce-psd2-payments-openapi.yml
operations:
- paymentRequestsPost
- paymentRequestConfirmationPost
- paymentRequestsGet
- paymentRequestTransactionsGet
- paymentRequestPut
generated: '2026-10-09'
method: generated
source: openapi/groupe-bpce-psd2-payments-openapi.yml
---

# Initiate and confirm a PSD2 payment (PISP)

1. Obtain a client-credentials token (`clientCredentials` scheme) as an eIDAS-certified PISP.
2. Submit the payment with `paymentRequestsPost`; redirect the PSU to the returned authorisation URL.
3. After PSU authentication, confirm with `paymentRequestConfirmationPost` (OAuth2 authorization code grant).
4. Poll status with `paymentRequestsGet` and list executed credit transfers with `paymentRequestTransactionsGet`.
5. Cancel a pending request with `paymentRequestPut`.

## Rules

- Every operation is grounded in an operationId present in `openapi/groupe-bpce-psd2-payments-openapi.yml`.
- Production calls go to the per-bank `oba-bad-me-live-api` hosts; the contract lists a sandbox server where one exists.
- Send the `X-Request-ID`/correlation headers the contract declares and handle 401/403/429 responses as declared; retries of POSTs are not documented as idempotent.
