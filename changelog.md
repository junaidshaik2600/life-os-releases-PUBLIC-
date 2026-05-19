# Life OS changelog

## 1.0.4 (build 23) — Reactive UX & cohesion

**Life OS 1.0.4 (build 23)** — polish release: screens stay in sync after edits. Recommended for anyone on 1.0.3 or earlier.

### Reactive surfaces

- **Dashboard** — Live chip counts for open todos and upcoming reminders.
- **Search** — Refreshes when core life data changes in the app.
- **Analytics** — Live dashboard bundle streams (no stale one-shot loads).
- **Diary** — Detail and recovery bin update without leaving the screen or manual refresh.
- **Reminders** — Live tab counts; calmer empty states.

### Unified refresh & widgets

- Central refresh path after todos, reminders, backup restore, and related edits.
- Android home-screen widgets pick up changes via debounced snapshot publish.

### Copy

- Calmer, consistent empty-state and reminder copy across the app.

### Carried from 1.0.3

- OTA install UX (finish only after real install, APK cleanup).
- Manifest reliability and Phase 1 branding/OTA from 1.0.2.

**APK:** `life-os-1.0.4.apk` · **Tag:** `v1.0.4` · **SHA256:** `2377280b7d5ec73ff99509c1be817ad9db561854ed4c6600e3e080c2f69b7a4e`

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
