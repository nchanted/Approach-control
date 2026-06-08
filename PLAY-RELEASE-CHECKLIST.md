# Google Play — Release Checklist for Approach

This is a practical checklist, **not legal advice**. A clean build does not guarantee
approval — Google reviewers apply judgment and policies change. Always check the
current Developer Program Policies: https://play.google.com/about/developer-content-policy/
and the Play Console for current requirements.

## What the app already does (low-risk profile)
- ✅ Requests **no permissions** (see AndroidManifest.xml).
- ✅ **No internet use** — the game is fully self-contained; no external/network requests
  (fonts and all assets are embedded in game.html).
- ✅ **No ads, analytics, tracking, or third-party SDKs.**
- ✅ **No in-app purchases** (paid-upfront model).
- ✅ Real airline/aircraft trademarks replaced with fictional equivalents.
- ✅ Progress/settings saved only in the app's private local storage.

## You MUST do before submitting
1. **Change the application ID.** It is currently `com.example.approach`, which Google
   rejects. Set it to a domain you control in `app/build.gradle.kts`, e.g.
   `com.yourname.approach`. Do this before generating the release build.
2. **Set version info** for each release: `versionCode` (integer, must increase every
   upload) and `versionName` (e.g. "1.0") in `app/build.gradle.kts`.
3. **Verify the target API level.** `targetSdk` is currently 34. Google raises the
   minimum required target SDK roughly yearly — confirm the current requirement in
   Play Console and bump if needed (Android Studio's upgrade assistant helps).
4. **Sign the release** with your own keystore and enrol in **Play App Signing**
   (prompted on first upload). Keep your keystore safe and backed up.
5. **Complete the Data Safety form** (see below).
6. **Content rating questionnaire** — answer honestly; this app rates for everyone.
7. **Store listing** — title, short/long description, and screenshots must match the
   app and must NOT contain real airline/manufacturer brand names or logos. Misleading
   metadata is a common rejection reason.
8. **Privacy policy** — host PRIVACY-POLICY.md (fill in the bracketed fields first) at a
   public URL and add it in the Play Console. A policy is recommended even when no data
   is collected, and some flows ask for a URL.

## Data Safety form answers (based on the current build)
- Does your app collect or share any user data? **No.**
- Is all user data encrypted in transit? **N/A — no data is transmitted.**
- Do you provide a way for users to request data deletion? Data is local only and is
  removed on uninstall / clearing app data. **No off-device data exists to delete.**

> If you ever add analytics, crash reporting, ads, internet features, or any SDK that
> phones home, these answers and the manifest permissions must be updated accordingly.

## Optional / situational
- **Designed for Families:** only opt in if you intend to target children. It triggers
  stricter requirements. The app's content is suitable for general audiences either way.
- **Pre-launch report / testing tracks:** use internal or closed testing first to catch
  device-specific issues before production.
