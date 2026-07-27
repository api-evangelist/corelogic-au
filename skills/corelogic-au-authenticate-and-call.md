---
name: Authenticate against the Cotality Australia APIs and make a first call
description: >-
  Mint a client_credentials JWT from the Cotality Access API and use it against any Australian
  property service, in the sandbox or in production. This is the prerequisite for every other
  CoreLogic Australia skill.
api: CoreLogic Australia Access API
grounding: collections/corelogic-au-sample-sandbox.postman_collection.json
generated: '2026-07-26'
method: generated
operations:
  - GET /access/oauth/token?grant_type=client_credentials
  - POST /as/token.oauth2
  - POST /oauth/token
  - GET /env/health
---

# Authenticate against the Cotality Australia APIs

Every Cotality Australia and New Zealand API is a bearer-token API behind an Apigee gateway. There
is no anonymous access: an unauthenticated request to any `*.api.cotality.com.au` host returns
`401` with `{"messages":[{"type":"ERROR","message":"Access token is missing"}]}`.

## Before you start

- Sign up at <https://developer.corelogic.asia/signup> and create a **sandbox client** at
  `/apps/create`. That is self-serve and gives you a client id and secret.
- Production and UAT credentials are **not** self-serve — they are provisioned only after a
  Cotality commercial data licence is signed.
- Requests must be HTTPS with TLS 1.2 or better.

## Pick the right host

| Environment | Token endpoint | Data host pattern |
|---|---|---|
| Sandbox | `https://api-sbox.corelogic.asia/access/as/token.oauth2` | `https://api-sbox.corelogic.asia/<service>` |
| UAT | `https://access.api-uat.cotality.com.au` | `https://<service>.api-uat.cotality.com.au` |
| Production | `https://access.api.cotality.com.au/as/token.oauth2` | `https://<service>.api.cotality.com.au` |

Tokens are **environment-bound**. A UAT token used against production returns
`401 "Invalid token provided."`, and a sandbox client calling UAT or production returns
`401 "Restricted environment access denied."`.

## Step 1 — get a token

Send your client id and secret as HTTP Basic (`base64(client_id:client_secret)`):

```
POST https://access.api.cotality.com.au/as/token.oauth2
Authorization: Basic <base64(client_id:client_secret)>
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials
```

Cotality's own published sandbox collection also shows the legacy form:

```
GET https://api.corelogic.asia/access/oauth/token?grant_type=client_credentials
```

## Step 2 — read the expiry off the JWT

The access token **is a JWT**. Decode it and read the `exp` claim (a Unix epoch timestamp) rather
than assuming a fixed lifetime — Cotality states plainly that "each grant_type token expiry is
subject to change without notice". Cache the token securely and refresh it before `exp`.

Do not try to derive entitlement from OAuth scopes. The data APIs request scope `openid` only;
what you are allowed to read is carried in JWT claims (`roles`, `geo_codes`, `authorities`)
provisioned against your licence.

## Step 3 — call a service

Send the token on every request:

```
GET https://property-details.api.cotality.com.au/au/properties/45232760/attributes/core
Authorization: Bearer <access_token>
```

Each service family also exposes an authenticated health probe at `<service-root>/env/health` —
useful for connectivity checks once you hold a token.

## Handle these responses

| Status | Meaning | What to do |
|---|---|---|
| 401 `Access token is missing` | No/unparseable Authorization header | Attach `Authorization: Bearer <jwt>` |
| 401 `Invalid token provided.` | Token minted in a different environment | Mint from the environment you are calling |
| 401 `Restricted environment access denied.` | Sandbox client hitting UAT/production | Call `api-sbox.corelogic.asia`, or licence up |
| 403 | Authenticated but not entitled | Your licence does not cover that product |
| 404 | Path does not exist | Check the service root in the environment table |
| 429 | Quota or rate limit exceeded | Retry with backoff — no `Retry-After` is published |

## Do not assume

There is no idempotency key, no request-id/correlation header, and no `Retry-After` or
`X-RateLimit-*` header on this surface. Build retries around plain exponential backoff.
