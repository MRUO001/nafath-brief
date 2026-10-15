Version: NAFATH-V1
Track: Cybersecurity

## Overview

A national single sign-on (SSO) service lets citizens use one account, from a mobile app or a website, to reach many government services. The six fields depend on each other. OpenID Connect tells each service who logged in, while OAuth 2.0 controls which APIs a service may call for the user. An AI model watches logins for fraud, but it must be governed so it does not lock out real citizens. The Android app should ask only for the permissions it needs, when it needs them. DNS over HTTPS protects the user's lookup of the login domain on untrusted networks. Oman's Personal Data Protection Law sets rules for the personal data the service collects.

## Software

OAuth 2.0 is an authorization framework. It gives a client an access token for limited access to resources, but it does not define a standard way to identify the user. OpenID Connect is an identity layer built on top of OAuth 2.0. It adds the "openid" scope and a signed ID Token that tells the service who logged in and when. So OpenID Connect is for user login, and OAuth 2.0 is for delegated access to resources.

Resource: OpenID Connect Core 1.0 incorporating errata set 2 - https://openid.net/specs/openid-connect-core-1_0.html

## AI

The NIST AI Risk Management Framework (AI RMF 1.0) has four functions: Govern, Map, Measure and Manage. For a model that flags suspicious logins, main risks are false positives that block real citizens, bias against groups such as travellers or VPN users, attackers learning to evade the model, privacy of login behaviour data, and decisions that cannot be explained. Before launch, the authority should measure error rates, keep human review for blocked users, and monitor the model after launch.

Resource: NIST AI 100-1, Artificial Intelligence Risk Management Framework (AI RMF 1.0) - https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf

## Mobile

Android has install-time permissions, which are granted automatically when the app is installed, and runtime ("dangerous") permissions, which protect private user data such as location, contacts, camera and microphone. For a runtime permission, the app must show a system prompt and the user can deny it. It must check the permission before each access, and should ask as late as possible, when the user starts the feature, for example when they tap "Scan QR code to log in".

Resource: Permissions on Android - Android Developers - https://developer.android.com/guide/topics/permissions/overview

## Networking

DNS over HTTPS (DoH) sends DNS queries and answers inside HTTPS, so they are encrypted and the DoH server is authenticated. This protects citizens on public Wi-Fi from attackers who watch their lookups or divert them to a rogue server. DoH does not hide queries from the DoH resolver itself, which can still link them to the user, and it does not prove that DNS answers are authentic; that is the job of DNSSEC.

Resource: RFC 8484 - DNS Queries over HTTPS (DoH) - https://www.rfc-editor.org/rfc/rfc8484

## Cybersecurity

Phishing-resistant authentication stops an attacker with a fake login page from capturing a credential they can reuse. CISA rates two forms as phishing-resistant: FIDO/WebAuthn (security keys or authenticators built into phones and laptops) and PKI-based methods such as smart cards. One-time codes from an app or token, push prompts, and SMS or voice codes do not qualify. A user can be tricked into giving them to a fake site, and SMS is also exposed to SIM swap and SS7 attacks.

Resource: Implementing Phishing-Resistant MFA (CISA fact sheet) - https://www.cisa.gov/sites/default/files/publications/fact-sheet-implementing-phishing-resistant-mfa-508c.pdf

## Data

Oman's Personal Data Protection Law (Royal Decree 6/2022, amended 2026) requires explicit consent (with some exceptions), a clear consent request naming the controller and data protection officer, risk controls and security measures, erasure when the purpose ends, breach notification to the Ministry and the citizen, and a Ministry permit for biometric data. Citizens may object to automated decisions and get human review. However, Article 3 excludes processing by state units performing their legal duties, so coverage needs checking.

Resource: Royal Decree 6/2022 Issuing the Personal Data Protection Law (Consolidated) - https://decree.om/2022/l20220006/

## Misconception in My Track

Common belief: any MFA stops phishing, so adding a one-time code from an authenticator app or SMS is enough. This is wrong. A one-time code still works on a fake site: CISA's example describes a user who types their password and the 6-digit code from their authenticator app into a look-alike login portal controlled by an attacker. CISA rates app-based codes as vulnerable to phishing, and only FIDO/WebAuthn and PKI-based methods as phishing-resistant. Proof: CISA, "Implementing Phishing-Resistant MFA", Table 1 "MFA Forms, Strongest to Weakest".

## Open Question

Which parts of the authority's login processing fall under the Article 3 government exemption in the amended PDPL, and does the citizen's Article 14 right to human review of automated decisions still apply to the AI fraud model?
