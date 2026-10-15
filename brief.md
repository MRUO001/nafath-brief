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

## Cybersecurity

## Data

## Misconception in My Track

## Open Question
