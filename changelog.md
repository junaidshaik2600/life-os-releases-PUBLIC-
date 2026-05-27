# Changelog

All notable changes to this project are documented in this file.

Release discipline: bump **`pubspec.yaml`** only for app version; run `.\scripts\release.ps1` for public `version.json` + changelog; update this file per release. See [docs/15-version-changelog-and-ota-tracking.md](docs/15-version-changelog-and-ota-tracking.md).

## 1.1.1 (2026-05-27) — build 53

### Added
- JSON import: per-type examples, add row, field legends (People, Places, Food, Watchlist, Dreams, Cabs)
- Cab cards: tap to open detail, swipe to delete
- In-repo documentation: APP-FLOW diagrams, page-reference manuals, lookup indexes

### Fixed
- Home widgets: transparent Android shell — wallpaper visible outside card (no #151A20 bars)
- Reminders button overflow; todo attachments viewer; Today tab open-only
- Share duplicate popup; watchlist label contrast
- Import refresh stability

### Changed
- Widget PNG aligned to top of launcher cell (fitStart)


## [1.1.0] - 2026-05-26 (build 52)

### feat

- **Todos:** Photo attachment thumbnails in detail sheet; tap for fullscreen viewer; attachment count chip on list cards.
- **Free time:** In-app image preview (pinch/zoom); clearer copy for PDFs and external files.
- **Import:** Cab memories from JSON (`cabs` key); flexible fields per row; warnings for unknown top-level keys.

### fix

- **Reminders:** Action row no longer overflows — Done + Snooze visible, Edit/Reschedule/Delete in menu; readable titles for URLs (e.g. YouTube Short).
- **Widgets:** Glance list content top-aligned — less empty band above single-line widgets.
- **Todos:** Marking done always sets parent `isDone`; completed tasks leave Today tab (open tasks only).
- **Todos:** `setDone` with subtasks now updates parent completion state.

## [1.0.10] - 2026-05-26 (build 51)

### fix

- **Widgets:** Calendar overflow on 6-row months (hide glance line, 146dp canvas, measured row heights).
- **Android:** Unique PendingIntent per widget instance — calendar always opens Diary, not last-updated widget target.

## [1.0.10] - 2026-05-26 (build 50)

### feat

- **Widgets:** Polished diary calendar widget (gradient, dynamic 5/6-week grid, today highlight, glance line, icon-only legend).

### fix

- **Widgets:** Calendar layout overflow fixed; scale-to-fit for resize.
- **Android:** Widget taps use single app task (`singleTask`) — no duplicate Life OS cards in Recents.

## [1.0.9] - 2026-05-26 (build 48)

Stabilization: watchlist & free time polish, structured share, diary calendar widget, backup/restore with app lock.

### feat

- **Watchlist:** Thumbnails, calmer YouTube open flow, colored status chips (Started / Stuck / Done), Free time shelf sync.
- **Free time:** Readable link subtitles; navigation to watchlist.
- **Share:** Structured destination sheet, oEmbed titles, Android finish-after-save.
- **Widgets:** Diary calendar home widget (month grid, entry dots).

### fix

- **Backup:** Restore no longer blocked by app lock resume.
- **Stability:** Safer provider refresh, todo sheet lifecycle, share/restore flows.

## [1.0.9] - 2026-05-19 (build 32)

### fix

- **Widgets:** Reverted native `RemoteViews` string/button pipeline; home-screen cards are now **Flutter-rendered** via `home_widget` (AppTheme surfaces, same copy as before). Android only shows the PNG + tap-to-open.

## [1.0.9] - 2026-05-19 (build 31)

Widget reliability, settings system shortcuts, and calmer dark surfaces.

### fix

- **Widgets:** Safe `updateAppWidget` fallback to minimal layout + logcat (`LifeOsWidget` tag); hardened `refreshFromSnapshotArgs`; no drawable backgrounds on widget action TextViews; placeholder when JSON missing; `reminders_future` channel field; publish no longer blocked while diary streak loads; dashboard sync on load.
- **Todos:** Priority chips show `P1 · Highly important` with stronger fills; menu color dots; top-3 border uses priority accent.
- **Notifications:** `ic_stat_lifeos` shape drawable for reliable scheduling icon.
- **UI:** Life Pulse hero and Reliable reminders card use lighter `surfaceContainerHigh` / tuned `primaryContainer` tokens.
- **Reminders:** `rescheduleAllPending()` on bootstrap/resume for background delivery.

### feat

- **Settings:** One-tap Android shortcuts for notifications, exact alarms, battery, and app info (`life_os/system_settings`).

### docs

- Widget troubleshooting and RemoteViews constraints in [19-widgets-living-surfaces.md](docs/19-widgets-living-surfaces.md).

## [1.0.7] - 2026-05-19 (build 26)

Surface coherence — living widgets, todo priority clarity, watchlist filters. No cloud, AI, or architecture rewrite.

### feat

- **Widgets:** Richer snapshot fields (diary mood/preview, Life Pulse insight line, people touch, P0 todo prefix); reminder widget uses `reminders_attention` so due-today items never show “nothing upcoming”; widget actions (todo done, reminder done/+15m snooze, diary write).
- **Todos:** P0–P5 priority bands with legacy normalization; execution status chips (not started / started / stuck).
- **Watchlist:** “Other” genre opens inline custom field; multi-filter sheet (genre, progress, labels, priority tiers); scan-friendly label chips with icons/colors.

### fix

- **Trust:** Reminder widget empty state aligned with open + due-today reminders (`ReminderService.snapshotForWidgets()`).

### docs

- [Living widget surfaces](docs/19-widgets-living-surfaces.md); index link from [docs/INDEX.md](docs/INDEX.md).

## [1.0.4] - 2026-05-19 (build 23)

Reactive UX and cohesion — screens stay in sync after edits without manual refresh. No new modules, cloud, or AI.

### feat

- **Dashboard:** Live chip counts for open todos and upcoming reminders (`dashboardBundleProvider`).
- **Search:** Refreshes when core life data changes (`ref.listen` on `lifePulseModelProvider`).
- **Analytics:** Uses live dashboard bundle streams instead of one-shot loads.
- **Diary:** Detail screen watches entry by id; recovery bin uses a reactive stream; editor invalidates detail on save.
- **Reminders:** Tab counts and calmer empty states via shared `AppCopy`.

### fix

- **Unified refresh:** `life_data_refresh.dart` centralizes provider invalidation after todos, reminders, backup restore, and related edits; `app_refresh.dart` re-exports for callers.
- **Home widgets:** Debounced `scheduleWidgetSnapshot()` after data changes so Android widgets pick up todo/reminder edits.
- **Copy:** Expanded calm, consistent strings in `app_copy.dart` (empty states, reminders, recovery).

### chore

- Release **1.0.4** for OTA from **1.0.3**; `minimum_supported_version` in manifest set to `1.0.3`.
- Carries **1.0.3** OTA install UX (deferred finish dialog, APK purge on success).

## [1.0.3] - 2026-05-17 (build 22)

### fix

- **OTA install UX:** “Update installed” only after system install completes; no early finish dialog; auto-delete downloaded APK (app + Downloads copy).
- **OTA manifest:** User-Agent, cache-bust, legacy URL fallback, clearer load errors.

### chore

- Release **1.0.3** for OTA testing from 1.0.2 / 1.0.1.

## [1.0.2] - 2026-05-16 (build 21)

Phase 1 completion: branding, release foundation, OTA hardening, premium trust.

### feat

- **Branding:** canonical icon at `assets/branding/app_icon.png`; `flutter_launcher_icons` (adaptive + monochrome); `app_branding.dart` for Life OS / Life Pulse / Life OS Premium; `ic_stat_lifeos` for notifications.
- **OTA:** native foreground APK download, progress UI, optional `apk_sha256` integrity check after download.
- **Premium trust:** `PremiumGate` / capability gating (Life Pulse memory, Analytics, widget rich fields); billing restore, expiry reconciliation, release-hidden promo codes.

### chore

- **Release signing:** `android/key.properties.example` + conditional release `signingConfig` in Gradle (debug fallback when no keystore).
- **Docs:** branding, signing/repos, Play internal-testing prep (`docs/16`–`18`).

### fix

- Search/navigation coherence; removed dead todo UI; premium copy consistency.

## [1.0.0] - 2026-05-14

### feat

- **In-app APK updates** (Settings → Tools → Check updates): cached manifest (faster repeat checks), download-once per version, **Install** when APK already on device, progress notification, copy to **Download/Life OS/updates/**, install via **FileProvider** + unknown-sources guidance.

### chore

- **Version 1.0.0** — single source of truth: `pubspec.yaml` `version:` only. Runtime reads semver via **`package_info_plus`** (`AppVersion`, `packageInfoProvider`); removed duplicate `AppConfig.currentVersion`. Android continues to use Flutter-injected `versionName` / `versionCode` from the same line.

## [0.4.0] - 2026-05-14

### feat

- **Google Play Billing** (`in_app_purchase`): product query, purchase stream, buy, restore; centralized product config in `AppConfig` + `billing_products.dart`.
- **Entitlements**: store/lifetime flags, **offline grace** window (`billingOfflineGraceDays`), **local trial** start from Premium (`billingDefaultTrialDays`), beta program flag; `EntitlementService` plans extended (trial, beta, admin, lifetime).
- **Premium UX**: Settings **Life OS Pro** card, **Premium & billing** hub (`premium_billing_screen.dart`), `PremiumBadge` and `LockedFeaturePreview` widgets; restore purchases wired to billing.
- **Privacy-safe telemetry**: capped local ring buffer for purchase/billing events (`purchase_telemetry.dart`) — no raw tokens.

### docs

- **`docs/12-premium-billing-and-play-console.md`**: code map, where to paste IDs, Console navigation, testing and publish checklist. **INDEX** and **10-centralized-configuration** updated for billing paths.

## [0.3.0] - 2026-05-12

### Release notes

This release focuses on **reliable backup and restore**, **Android widgets**, **shell privacy** (so file pickers no longer dispose Settings mid-flow), and a **broader encrypted backup payload** (diary, people, places, todos, reminders, tags, links, work, watchlist, food, media attachment *rows*, and more). **0.3.0** is suitable for day-to-day builds; two areas remain intentionally incomplete:

- **Backup and restore:** Encrypted `.enc` archives are portable when you use a **password**; device-key backups remain same-install only. Payload v2 restores many tables and rebuilds diary FTS after import. **Binary media files** (photos, banners, attachment files on disk) are **not** bundled inside the archive—only **metadata paths** are restored, so attachments may show as missing until you re-add files or re-export from a device that still has them. A future milestone may add optional media bundling or clearer UX around broken paths.
- **Media attachments:** Row-level backup/restore is included; **file bytes** and cross-device path migration are **not** solved in this version.

### feat

- Full-shell **privacy curtain** on `paused`/`hidden` while unlocked: keeps the main `PageView` (and Settings) **mounted** so restore, pickers, and other async flows complete instead of dying on `context.mounted`.
- Android **`FLAG_SECURE`** toggle via `life_os/privacy` method channel for recents/screenshot hardening when the curtain is active.
- **`rootShellTabRequestProvider`** and post-restore **“Open Diary”** navigation.
- Restore **preview + confirm** dialog (decrypted counts, export time) before writing the database.
- **`flutter_secure_storage`**-backed device backup key (optional path); password exports tagged `key_kind` in envelope.
- **`post_restore_refresh`**: invalidates repository and service providers after restore (keeps the same open SQLite connection so restored data stays visible).
- Pull-to-refresh on dashboard, diary, people, library hub, todos; `PageView` uses non-swipeable physics for stable bottom nav.
- Life pulse / intelligence / search stack additions and widget snapshot publishing refinements (see lib and docs).

### fix

- **Backup restore (V3):** integrity check now uses the **raw `data.json` bytes** in the ZIP (matches export); avoids false “integrity failed” after decode/re-encode drift.
- **Backup restore (UI):** after restore, the app no longer **closes and reopens** the Drift database by default, so merged rows reliably appear without an empty flash.
- **Photos:** diary backdrop, place photos, todo photo attachments, and `MediaService.pickAndAttach` use **gallery / photo picker only** — removed Documents-style “choose image file” paths for those surfaces. `file_picker` remains for backups, notification sounds, Free Time files, etc.

### docs

- Added **`docs/11-image-picking-and-media.md`** and linked it from **INDEX** and a **Maintainer atlas** footer across the doc set so contributors can find code locations quickly.

### fix (continued)

- **Critical:** Restore from backup no longer silently aborts when the system file picker backgrounds the app (previously `_phase == checking` disposed Settings).

### infra / Android

- Package namespace move toward **`com.lifeos`**; widget providers, storage channel, widget scheduler/refresh workers as applicable.
- Public export path for backups/PDFs under Downloads where supported.

## [0.2.0] - 2026-05-11

### infrastructure
- App update manifest architecture: semver compare, `minimum_supported_version`, optional HTTPS URL via `AppConfig.updateManifestUrl` (no auto-installer yet).
- Backup envelope v2 with HMAC integrity; legacy v1 restores still supported; export to user-chosen folders (encrypted + JSON).
- `EntitlementService` + `AppCapability` matrix; `BillingVerification` placeholder for future Play Billing.
- Expanded `AppFeatures` for premium, AI, sync, exports, widgets, and beta flags.
- Android `life_os/storage` channel for free-space probe; storage health dialog in Settings.
- Release docs: version manifest example, release note template, widget architecture notes.

### docs
- `docs/releases/version-manifest.example.json`, `TEMPLATE.md`, `README.md`, `android-widgets.md`.

## [0.1.0] - 2026-05-10

### security
- Hardened app lock lifecycle ordering so protected content is obscured before auth flows.
- Tightened lock resume handling to reduce accidental route exposure.

### fix
- Corrected birthday "This month" filtering to exclude already passed birthdays in the current month.
- Removed stale People analytics action entry that had low daily-use value.

### ui
- Improved completed todo hierarchy cards with restore and permanent-delete actions.
- Added reversible todo completion behavior with undo snackbar.
- Updated removed-people destructive action styling to stronger danger emphasis.

### feat
- Added extended respect values (`very_high`, `high`, `neutral`, `low`, `very_low`) and People respect filtering.
- Expanded Android widget registration suite (todos, birthdays, reminders, diary, actions).

### docs
- Added release docs under `docs/releases/`.
- Added release/versioning and icon tooling notes.

