# Urobi – Compliance Overview

This document summarizes how Urobi is designed to comply with Apple App Store guidelines and applicable data protection law. It is a plain-language overview and does not replace the [Terms & Conditions](terms-and-conditions.html) or [Privacy Policy](privacy-policy.html), which remain the legally binding documents.

## 1. App Store Guidelines

- **Payments (Guideline 3.1.1):** All purchasable digital content (credit packs) is sold exclusively through Apple's In‑App Purchase (StoreKit 2). No external payment links, alternative payment mechanisms, or account-based subscriptions are used.
- **Consumables, not subscriptions:** Credit packs are one-time, consumable purchases. There is no auto-renewing subscription, so there is no recurring billing to manage or cancel.
- **Transparent pricing (Guideline 3.1.2):** Prices and the approximate number of AI requests per pack are always displayed in the app before purchase, in the user's local currency.
- **Support URL (Guideline 1.5 / App Store Connect metadata):** A single, always-available Support URL is provided (this documentation site's [User Manual](user-manual.html)), covering usage instructions, troubleshooting, and a direct contact email.
- **Privacy Nutrition Label / App Privacy details:** Data types collected (device identifier, usage/diagnostics data) are declared accurately in App Store Connect and match the [Privacy Policy](privacy-policy.html).
- **Third-party content disclosure (Guideline 5.1.1):** The use of a third-party AI provider (OpenAI) is disclosed in-app before first use, and consent is required before any data is transmitted.

## 2. GDPR / Data Protection (EU Users)

- **Legal basis:** Processing of anonymous device data is based on the necessity to perform the service you request (Art. 6(1)(b) GDPR) and, for AI-processing of your images/voice, your explicit consent (Art. 6(1)(a) GDPR), collected via an in-app consent screen before first use.
- **Data minimization:** Only an anonymous device ID, credit/usage metadata, and short-lived security tokens are stored. No name, email, or precise location is collected.
- **Processor relationship:** OpenAI, L.L.C. acts as a data processor for AI inference requests, bound by its own [Privacy Policy](https://openai.com/policies/privacy-policy) and standard contractual safeguards for international transfers (the servers are located in the United States).
- **Data subject rights:** Because no personal account exists, most requests (access, deletion) are fulfilled by identifying the anonymous device and, on request, purging its associated records. Contact [robert_schirmer@gmx.de](mailto:robert_schirmer@gmx.de) to exercise these rights — see the Privacy Policy for full detail.
- **Retention:** Usage logs and credit transaction history are retained only as long as necessary for billing/fraud-prevention purposes; no image, voice, or AI-response content is retained at all.

## 3. Children's Privacy

- Urobi is not directed at children under 13 (or the equivalent minimum age in your country) and does not knowingly collect personal data from them. See the [Privacy Policy](privacy-policy.html) "Children" section for full detail and how to report a concern.

## 4. Accessibility Compliance

- Urobi is built as an assistive tool for blind and low-vision users and follows Apple's Human Interface Guidelines for Accessibility: full VoiceOver labeling, Dynamic Type-friendly layout, and audio-first feedback for every result.

## 5. Sub-processors

| Sub-processor | Purpose | Location |
|---|---|---|
| OpenAI, L.L.C. | AI image analysis, text generation, text-to-speech | United States |
| Apple Inc. (App Store / StoreKit) | Payment processing for credit packs | Global (Apple infrastructure) |
| Hosting provider for the Urobi backend | Application hosting, database, reverse proxy | EU |

## 6. Document Index

- [User Manual](user-manual.html) — how to use the app (this is the App Store Support URL destination)
- [Privacy Policy](privacy-policy.html)
- [Terms & Conditions](terms-and-conditions.html)
- [Security Overview](security.html)

---

*This Compliance Overview was last updated on 2026-07-19 and is reviewed periodically as the app evolves.*
