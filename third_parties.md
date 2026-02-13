# Third-Party SDKs and Services

This document lists third-party SDKs, services, and integrations used (or commonly considered) for AI Surf Coach and what data they typically collect. Use this to prepare App Store Connect disclosures and the public privacy policy. Only list SDKs you actually integrate; remove examples that do not apply.

Template entry format:
- Name: SDK / Service name
- Purpose: Short description of why it is used in the app
- Data collected: Types of data the SDK/service collects (e.g., device identifiers, crash logs, analytics events, IP address, media uploads)
- Is data linked to a user identity?: yes / no / depends (explain)
- Is data shared with third parties?: yes / no / depends (explain)
- Retention: Typical retention or how we configure it
- Where documented: Link to vendor privacy policy / docs
- Integration notes: SDK version, platform (iOS/Android/web) and any special privacy settings to enable

---

## Example entries

- Name: Firebase (Google)
  - Purpose: Analytics, crash reporting (Crashlytics), optional remote config
  - Data collected: Device identifiers (Instance ID), device model, OS version, crash stack traces, basic analytics events, IP address
  - Is data linked to a user identity?: Depends — can be linked if you pass user identifiers to Firebase (avoid passing PII)
  - Is data shared with third parties?: Google processes data; configured under Google terms
  - Retention: Configurable in Firebase console; default varies by product
  - Where documented: https://policies.google.com/privacy
  - Integration notes: iOS/Android SDKs; disable or limit analytics if strict privacy mode is enabled

- Name: Stripe
  - Purpose: Payments processor for subscription and in-app purchases handled server-side
  - Data collected: Payment card information (handled by Stripe.js or SDK), billing email, transaction metadata
  - Is data linked to a user identity?: Yes (transaction records), but card data is handled by Stripe and not stored on our servers if using tokenization
  - Is data shared with third parties?: Stripe processes payment data per their policy
  - Retention: Managed by Stripe; our server stores transaction metadata as needed
  - Where documented: https://stripe.com/privacy
  - Integration notes: Use client-side tokenization; do not log full card numbers

- Name: Sentry (or Rollbar)
  - Purpose: Crash reporting and error monitoring
  - Data collected: Stack traces, breadcrumbs, device info, optionally user identifiers if configured
  - Is data linked to a user identity?: Depends on configuration; avoid sending PII
  - Is data shared with third parties?: Sentry is a third-party processor
  - Retention: Configurable in the Sentry account/project settings
  - Where documented: https://sentry.io/privacy/
  - Integration notes: Scrub PII from events; enable server-side filtering

- Name: Agora / Twilio (real-time audio/video)
  - Purpose: Real-time streaming or remote coaching sessions
  - Data collected: Media streams (audio/video), connection metadata, network addresses
  - Is data linked to a user identity?: Depends on implementation; media streams may contain PII
  - Is data shared with third parties?: Media is proxied/processed by the service provider
  - Retention: Usually transient unless recordings are enabled; document recording retention if used
  - Where documented: https://www.agora.io/en/privacy/  https://www.twilio.com/legal/privacy
  - Integration notes: Provide explicit consent before enabling live streaming or recording; document how recordings are used and retained

---

## How to use this file
- Before submitting to the App Store, ensure this file lists every third-party SDK/service the app bundle includes.
- Use the data collected fields to fill App Store Connect's "Data Collected" and "Third-Party Advertising" sections.
- Keep SDK versions and documentation links up to date.

## Add a new SDK
When adding a new third-party SDK to the project, add an entry with the template fields above and link to the vendor's privacy docs.

# Disclaimer
This document is a developer aid and not a substitute for legal advice. For compliance questions or legal wording for the public privacy policy, consult with legal counsel.