Version: NAFATH-V1
Track: AI
## Overview
A national single sign-on service must provide a consistent identity journey across the website and mobile app while limiting access to each government service. OpenID Connect confirms the authenticated user's identity, while OAuth 2.0 authorizes limited access to protected resources. The mobile app should request sensitive Android permissions only when a feature genuinely needs them. Network protections such as DNS over HTTPS can reduce exposure of DNS lookups, but they cannot replace secure connections or phishing-resistant authentication. An AI model may help flag unusual sign-ins, yet it should be tested for reliability, bias, privacy, security, and human oversight, with ongoing monitoring. Because login records and identity details are personal data, the authority must also apply Oman's data-protection requirements throughout collection, use, storage, sharing, and retention. For the AI track, the key design issue is managing model risk before and after deployment.

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
DNS over HTTPS (DoH) sends DNS queries and responses over HTTPS between a device and its chosen resolver. Encryption protects the exchange in transit, making it harder for observers on that path to read or alter lookups. DoH does not hide queries from the resolver, conceal the device's IP address or all later connections from network observers, or replace HTTPS for the government website. It protects one layer of DNS privacy, not anonymity.

Resource: RFC 8484: DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484.html

## Cybersecurity
Phishing resistance requires the authentication protocol to prevent an impostor verifier from obtaining usable authentication secrets or outputs without relying on the user's vigilance. FIDO2/WebAuthn authenticators can meet this through verifier-name binding: the cryptographic response is tied to the legitimate site's origin. Manually entered SMS, email, or authenticator-app OTPs are not phishing-resistant because a fake site can relay them. Ordinary push approval is also not enough unless the protocol provides verifier binding.

Resource: NIST SP 800-63B-4: Authentication and Authenticator Management - https://pages.nist.gov/800-63-4/sp800-63b.html

## Data
Under Oman's Personal Data Protection Law, processing generally requires explicit consent unless a legal exception applies. Before processing, the controller must notify the data subject in writing of the controller, purpose, source, and main rights. The controller and processor must keep data confidential, report breaches, retain records only as required by law, and follow restrictions on transfers outside Oman. Sensitive data has special rules.

Resource: Royal Decree No. 6/2022 Promulgating the Personal Data Protection Law - https://mjla.gov.om/laws/ar/1/show/183

## Misconception in My Track
A common misconception is that a login-risk model is ready for launch once it achieves high accuracy. NIST's AI RMF 1.0, in Section 2.3 "Trustworthy AI Characteristics," says trustworthy AI systems are "valid and reliable, safe, secure and resilient, accountable and transparent, explainable and interpretable, privacy-enhanced, and fair with harmful bias managed." This shows that accuracy alone is not enough. For this service, the authority should test bias, privacy, security, reliability, and human oversight under realistic login conditions before deployment.

## Open Question
How will the authority set an acceptable false-positive rate for login challenges without unfairly burdening users with limited connectivity or shared devices?

