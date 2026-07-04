
# IAM SSO Federation Lab — SAML and OIDC/OAuth 2.0

## Overview
Configures Microsoft Entra ID as an Identity Provider for two test
applications — one using SAML 2.0, one using OIDC/OAuth 2.0.
Captures and decodes real tokens from both protocols and documents
the structural differences between an XML assertion and a JWT.

## Protocols covered
- SAML 2.0 — XML-based, browser redirect flow, enterprise apps
- OIDC — JWT-based, REST-friendly, modern apps
- OAuth 2.0 — Auth code + PKCE flow tested via Postman

## Structure
docs/               # Protocol notes and comparison document
collections/        # Postman collection JSON
evidence/           # Decoded tokens and captured assertions

## Key learnings

- SPA app type in Entra ID cannot exchange auth codes via server-side tools
  like VS Code REST Client — Mobile and desktop app type is required for
  REST-based token exchange flows

- Auth codes expire in 10 minutes — have the request file fully prepared
  before getting the code, then paste and send within 60 seconds

- SAML assertion is 150+ lines of verbose XML — JWT is 12 lines of JSON
  Both carry the same user identity information in completely different formats

- The nonce claim in OIDC must always be set — it prevents replay attacks
  by binding the token to the specific request that generated it

- oid is the most reliable user identifier in a JWT — UPN can change when
  a user gets married or changes name, oid never changes

- SAML certificates need periodic renewal — expiry causes SSO outages
  and is one of the most common production incidents in enterprise IAM

- GitHub blocks pushes containing real tokens and assertions — always
  add evidence files containing live tokens to .gitignore before committing

- SPA redirect URI and Mobile/desktop redirect URI behave differently
  in Entra ID — the app type controls which token redemption flows are allowed

- Both SAML and OIDC can run simultaneously from the same Entra ID tenant
  — no separate configuration needed, just different app registrations
'@ | Add-Content -Path .\README.md -Encoding UTF8
