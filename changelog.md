# Changelog

All notable changes to this project are documented in this file.

Release discipline: bump **`pubspec.yaml`** only for app version; run `.\scripts\release.ps1` for public `version.json` + changelog; update this file per release. See [docs/15-version-changelog-and-ota-tracking.md](docs/15-version-changelog-and-ota-tracking.md).

## [1.1.5] - 2026-05-27 (build 57)

### fix

- **Form stability (trust pass):** Reminders, Cabs, and Free time forms use StatefulWidget-owned controllers — save runs after modal close; fixes `_dependents.isEmpty` and disposed-controller crashes on Cancel/back.
- **Cabs place picker:** Guards `mounted` after async place sheet before writing to controllers.
- **Widget layout:** Birthdays show **3 names** then `+N more` (was capped at 2); Life Pulse order **todos → birthdays → reminders**; compact lists vertically centered; `+N more` overflow row on glance tiles.
- **Diary widget badge:** Sanitizes reference tokens — no raw `[[people|…]]` syntax on home-screen tile.

### test

- **Trust pass:** `test/trust_pass_test.dart` + `test/backup_v3_roundtrip_test.dart` — 21/21 green.

### release

- **APK signing:** v1.1.5 ships **release-signed** with keystore alias `lifeos` — signer **Shaik Mohammad Junaid · Life OS**.
- **Settings → App info:** Shows **Signed by: Shaik Mohammad Junaid · Life OS** on device (debug builds show Android Debug).

## [1.1.4] - 2026-05-27 (build 56)

### feat

- **Todo attachments:** Added a swipeable gallery viewer for multiple attachments so you can slide to next/previous without backing out each time.
- **Attachment support:** Todo and Free time flows now handle image, video, audio, text, and PDF more clearly in-app (PDF with external-open fallback).
- **People widget:** Replaced generic memory copy with this-month interaction ranking (top 3 contacts).

### fix

- **Life Pulse widget:** Center copy is now split into 3 balanced lines (`reminders`, `todos`, `birthdays`) for better readability on small tiles.
- **Today todos:** Tasks completed from Today now remain visible in Today (grouped at bottom under done), matching common task-app behavior.
- **Subtask ordering:** In task cards, unfinished steps stay on top and completed steps move below automatically.

## [1.1.3] - 2026-05-27 (build 55)

### fix

- **Widgets (visual pass):** Birthday/Diary/Pulse/Todos/Reminders body rows support plain text mode (no forced bullet rows) to match card preview styling.
- **Diary widget:** Header favors today's entry title; body shows short summary above journal preview (editor section order unchanged: Morning → Dream → Short summary → Full journal).
- **Widget typography:** Bulleted body lines with accent-colored dots; peach reminder lines; P0/overdue todo lines in salmon; centered empty/hint text for Life Pulse, People, and Birthdays — matches reference home-screen cards.
- **Life Pulse widget:** Center text uses two-line balanced copy instead of one long row for cleaner readability.
- **People widget:** Shows this month's interaction ranking (top 3 people by diary interactions).
- **Attachments:** Todo and Free time now support in-app viewing for image/video/audio/text; PDFs open in-app with external-open fallback.
- **Diary widget tap:** Opens today's diary entry editor directly (`diary_today`) instead of only switching to diary tab.
- **Life Pulse copy:** Streak stays in badge; body keeps explicit `todos · reminders · birthdays` counts including zeros.
- **Calendar widget size:** Reduced logical and provider dimensions for a lighter home-screen footprint.
- **Stability:** Reminders, Free time, and Cabs save **after** the dialog/sheet closes (no DB writes while the form is still open) — fixes `_dependents.isEmpty` when typing and saving.
- **Diary editor:** Section order is Morning & routine → Dream → Short summary → Full journal (short summary directly above full journal).

## [1.1.2] - 2026-05-27 (build 54)

### fix

- **Widgets (Option B):** Glance PNG height follows launcher cell (`OPTION_APPWIDGET_MIN_HEIGHT`); bitmap fills cell (`fitXY`) — removes outer `#151A20` letterbox bands.
- **Widgets (layout):** Sparse body lines vertically centered in body zone; empty state uses hint + white dot row (no duplicate badge summary in accent under divider).
- **Widgets:** Reverts hollow top-cramped look from Option A-only (`fitStart` on fixed 88dp PNG).

## [1.1.1] - 2026-05-27 (build 53)

### feat

- **Import:** Per-type JSON examples (all supported fields), “Add row”, type selector, and field legend in Settings → Import written data.
- **Cabs:** Tap card for detail sheet; swipe left to delete (like People).
- **Docs:** Full in-repo documentation — app flow diagrams, page manuals, button/search/class lookup indexes.

### fix

- **Share:** Removed useless “Open Life OS” sheet action; reduced duplicate share popup.
- **Watchlist:** Label chips (including “Free time”) use readable contrast colors.
- **Widgets:** Transparent Android launcher shell (`life_os_widget_image.xml`) — wallpaper shows in outer gaps instead of `#151A20` bars; `fitStart` aligns card to top.
- **Stability:** Safer refresh after import (reduces `_dependents.isEmpty` assertion risk).

### docs

- `docs/APP-FLOW.md`, `docs/DOCUMENTATION-MAP.md`, `docs/page-reference/*` — beginner and pro navigation paths.

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

