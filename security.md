# Urobi – Security Overview

This document explains, in plain language, how Urobi protects your data. It is intended for users, reviewers, and partners who want to understand the technical safeguards behind the app.

## 1. No Accounts, No Passwords

Urobi does not use email/password accounts. Each device generates a random, anonymous identifier (UUID) on first launch, stored in the iOS **Keychain** (not in plain app storage), which cannot be linked back to your Apple ID, name, or any personal identity.

## 2. Transport Security

- All communication between the app and the Urobi backend happens over **HTTPS/TLS**, enforced by iOS App Transport Security (ATS). Plain HTTP is only permitted to `localhost` for local development builds and is never used in production.
- The backend is fronted by an **nginx reverse proxy** with a valid TLS certificate, HSTS, and modern cipher configuration.

## 3. Request Authentication

- On registration, each device receives a unique **HMAC secret**, stored securely on-device. Every API request is signed with this secret, so requests cannot be forged or replayed by a different device.
- Short-lived **JWT access tokens** (issued after registration) authorize each request; a separate long-lived **refresh token** (30 days) is used only to obtain new access tokens, never to authorize requests directly.
- The backend independently verifies the HMAC signature and JWT on every request before processing it.

## 4. Rate Limiting & Abuse Prevention

- The backend enforces **quota and rate-limit middleware** per device to prevent abuse of the AI pipeline.
- **fail2ban** is deployed at the infrastructure level, automatically blocking IPs that show authentication abuse or excessive request-rate patterns (see `fail2ban/jail-urobi.local` and the custom filters for auth/rate-limit violations).
- Devices can be blocked server-side (`is_blocked`) if abuse is detected, without affecting other users.

## 5. Data Minimization

- Urobi's backend does **not** store photos, voice recordings, or AI-generated text. These are processed in-memory for the duration of a single request and then discarded.
- Only minimal, anonymous metadata is persisted: device ID, tier, credit balance, per-request token counts/cost estimates, and timestamps — used solely for billing accuracy and fraud prevention.
- Voice input is transcribed **on-device** using Apple's Speech framework; only the resulting text (never raw audio) is transmitted.

## 6. Database & Infrastructure Security

- The backend database (PostgreSQL) is accessed exclusively over encrypted connections and is not exposed directly to the internet.
- The backend runs in isolated Docker containers (see `docker-compose.yml` / `Dockerfile`), separating the API, database, and reverse proxy.
- Admin access to the internal dashboard requires a separate authenticated admin account, distinct from device credentials.

## 7. Third-Party Processing

- AI requests (image analysis, text generation, text-to-speech) are forwarded from our backend to **OpenAI, L.L.C.**, acting as a data processor, strictly to fulfil the request you initiated. OpenAI does not receive your device identity, only the content needed to answer the request.
- No other third parties receive your content. Purchases are handled entirely by Apple; Urobi never sees or stores payment card details.

## 8. Responsible Disclosure

If you discover a security vulnerability in Urobi or its backend, please report it responsibly and privately before any public disclosure:

**Email:** [robert_schirmer@gmx.de](mailto:robert_schirmer@gmx.de)

We aim to acknowledge reports within 5 business days.

## 9. Related Documents

- [Privacy Policy](privacy-policy.html)
- [Terms & Conditions](terms-and-conditions.html)
- [Compliance Overview](compliance.html)
- [User Manual](user-manual.html)

---

*This Security Overview was last updated on 2026-07-19.*
