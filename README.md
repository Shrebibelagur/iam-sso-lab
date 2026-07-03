@'
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
(updated as the project progresses)
'@ | Set-Content -Path README.md -Encoding UTF8