Version: NAFATH-V1
Track: AI
## Overview
A national single sign-on service must provide a consistent identity journey across the website and mobile app while limiting access to each government service. OpenID Connect identifies the authenticated user, while OAuth 2.0 authorizes limited access to protected resources. The mobile app should request sensitive Android permissions only when a feature genuinely needs them. Network protections such as DNS over HTTPS can reduce exposure of DNS lookups, but they cannot replace secure connections or phishing-resistant authentication. An AI model may help flag unusual sign-ins, yet it should be tested for reliability, bias, privacy, security, and human oversight, with ongoing monitoring. Because login records and identity details are personal data, the authority must also apply Oman's data-protection requirements throughout collection, use, storage, sharing, and retention. For the AI track, the key design issue is managing model risk before and after deployment.

## Software
OAuth 2.0 is an authorization framework that allows a client to obtain limited access to a protected resource on a user's behalf. By itself, it does not provide a standard way for the client to verify the user's identity. OpenID Connect (OIDC) adds an identity layer on top of OAuth 2.0 and uses an ID Token to convey authentication information. Therefore, OIDC is designed for user login, while OAuth 2.0 supports delegated access to APIs.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0-errata2.html

## AI
Use NIST's Govern, Map, Measure, and Manage functions before launch. Assign accountability, define the intended use and affected users, identify potential harms, and choose controls. Test false alarms and missed attacks across user groups and realistic login conditions. Assess privacy, security, reliability, explainability, and fairness, not accuracy alone. Require human review for consequential account blocks, document residual risks, and monitor performance and model drift after deployment.

Resource: Artificial Intelligence Risk Management Framework (AI RMF 1.0) - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf

## Mobile
Android distinguishes normal permissions from dangerous ones, which protect sensitive data or actions. Normal permissions are generally granted automatically; for modern apps targeting API level 23 or higher, dangerous permissions require a runtime request. A manifest declaration alone does not grant access. The app should request a permission in context, when a feature needs it, and explain why. If the user denies it, that access remains unavailable. A login app should not request unrelated location or contact access.

Resource: Request runtime permissions - https://developer.android.com/training/permissions/requesting

## Networking
## Cybersecurity
## Data
## Misconception in My Track
## Open Question
