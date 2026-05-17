# Life OS changelog

## 1.0.2 (build 21) — Phase 1: branding & release foundation

**Life OS 1.0.2 (build 21)** completes Phase 1: production identity, release discipline, and trust layers—without new cloud, AI, or major modules. Aimed at premium-alpha testers and sideload/OTA installs.

### Branding & identity

- Unified naming: **Life OS** (app), **Life Pulse** (home dashboard), **Life OS Premium** (subscription tier).
- Refreshed launcher icons (adaptive + monochrome) from the canonical brand asset.
- Consistent notification icon for reminders, update checks, and APK download progress.
- Splash and Settings About copy aligned with the brand.

### In-app updates (OTA)

- Check for updates from Settings via the public `version.json` manifest.
- Background APK download (foreground service) with progress in the dialog and notification.
- Optional SHA-256 verification after download when the manifest includes `apk_sha256`.
- Clear install flow and guidance to fully close and reopen the app after install.

### Premium trust & billing

- Premium features gated through a single capability system with calm lock UI.
- Gating in Life Pulse memory, Analytics, and rich home-screen widget fields.
- Billing lifecycle: restore purchases, expiry handling, offline grace.
- Promo / tester codes hidden in release builds.

### Product polish

- Search and navigation fixes; removal of dead or non-functional UI in places.
- Clearer premium copy across Settings.

### What did not change

- No cloud sync, AI, or new major modules.
- Encrypted backups still store attachment metadata, not full media file bytes.

### Install / update

- **Fresh install:** GitHub Release **v1.0.2** → `life-os-1.0.2.apk`
- **From 1.0.1 or older:** Settings → Check for updates → Download → Install → fully close app → reopen
- **Already on 1.0.2:** OTA uses semver only; reinstall APK manually for this rebuild (build 21)
