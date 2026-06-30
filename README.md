# Fit Hunter Releases

**Latest Version:** 1.0.0 (stable)
**Date:** 2026-06-30

[⬇️ Download APK](https://github.com/walisoncm/fit_hunter-releases/releases/download/v1.0.0/fit_hunter_1.0.0.apk)

## Release Notes

# Release Notes - v1.0.0

## 🎉 First Stable Release

Fit Hunter leaves beta and launches as a full, stable experience. This release marks the culmination of all beta improvements and introduces the monetization system.

## 💎 Hunter Premium

- **Ad-supported free tier**: contextual interstitial ads shown after daily quest completion, level up, and dungeon reward claim — never interrupting active gameplay.
- **Hunter Premium subscription**: annual plan that removes all ads permanently, unlocks the Premium badge, and extends health stats history to 30 days.
- **Paywall**: clean RPG-styled bottom sheet displaying benefits and the annual price fetched live from the store.
- **Automatic paywall**: shown after every 5 ad views in a session to encourage upgrade.
- **Restore Purchase**: one-tap recovery of an active subscription after reinstall or device change.
- **Premium badge**: golden crown icon displayed next to the hunter's name on the profile screen and in all chat bubbles (global, guild, party, private).
- **Extended health history**: Premium users access 30 days of local health stats; free users see 7 days.
- **Server-side validation**: premium status is verified via RevenueCat webhook → Supabase Edge Function, preventing client-side bypass.

## 🛡️ Security & Infrastructure

- New `subscriptions` audit table recording every RevenueCat lifecycle event (purchase, renewal, cancellation, expiration).
- `is_premium` field on `hunter_profiles` updated exclusively by the server — never by the client.
- RevenueCat webhook Edge Function deployed with `Authorization` header validation.

---
*This repository is automatically updated by CI/CD.*
