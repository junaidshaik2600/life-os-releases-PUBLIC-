# Life OS — Public releases

Official **Android update channel** for [Life OS](https://github.com/junaidshaik2600/life-os-app-PRIVATE-): release APKs, OTA manifest, and release notes.

> **This is not the app source code.**  
> The Flutter project lives in the private development repository. This repo exists so installs can **check for updates** and **download new APKs** safely.

---

## What is Life OS?

**Life OS** is a calm, **offline-first** personal life operating system:

- Diary and memory
- People and relationships
- Todos, reminders, places, and more
- Local data on your device (SQLite)
- Home-screen widgets and encrypted backup

**Android package:** `com.lifeos`

---

## Get the latest version

### In-app update (recommended)

If Life OS is already installed:

1. Open **Settings**
2. Tap **Check for updates**
3. **Download** → **Install**
4. Fully close the app (remove from recents) → open again

The app reads **`version.json`** from this repository (see [OTA manifest](#ota-manifest-versionjson) below).

### Manual install

1. Open **[Releases](https://github.com/junaidshaik2600/life-os-releases-PUBLIC-/releases)**
2. Download the newest **`life-os-x.y.z.apk`** (release build, ~75–80 MB)
3. Open the file on your phone and install (allow “unknown apps” if Android asks)

---

## Current release

| | |
|---|---|
| **Version** | **1.1.5** (build **57**) |
| **APK** | [life-os-1.1.5.apk](https://github.com/junaidshaik2600/life-os-releases-PUBLIC-/releases/download/v1.1.5/life-os-1.1.5.apk) |
| **SHA256** | `2ec8e2720f928b71a0832cb63b216e760ca3272e12aceeb0197d95799283f69d` |
| **Signed by** | Shaik Mohammad Junaid · Life OS |

Verify on device: **Settings → App info → Signed by: …**

---

## OTA manifest (`version.json`)

The app fetches this file from the **`main`** branch:

```
https://raw.githubusercontent.com/junaidshaik2600/life-os-releases-PUBLIC-/main/version.json
```

### Fields

| Field | Purpose |
|-------|---------|
| `latest_version` | Newest semver offered to users (e.g. `"1.1.5"`) |
| `build_number` | Android `versionCode` (e.g. `57`) |
| `minimum_supported_version` | Oldest version still supported; older installs see an extra “please update” notice |
| `apk_url` | Direct HTTPS link to the **release** `.apk` on GitHub Releases |
| `sha256` | SHA-256 hex of the APK file (integrity check after download) |
| `release_notes` | Short text shown in the update dialog |

### Example

```json
{
  "latest_version": "1.1.5",
  "build_number": 57,
  "minimum_supported_version": "1.1.0",
  "apk_url": "https://github.com/junaidshaik2600/life-os-releases-PUBLIC-/releases/download/v1.1.5/life-os-1.1.5.apk",
  "sha256": "2ec8e2720f928b71a0832cb63b216e760ca3272e12aceeb0197d95799283f69d",
  "release_notes": "Life OS 1.1.5 (57): stability and widget layout improvements."
}
```

### Maintainer rules

- Only publish **release-signed** APKs here (~75–80 MB, **Life OS** signer). Do **not** upload debug builds (~170 MB, Android Debug).
- Bump **`latest_version`** when you ship a version users should install.
- The filename in **`apk_url`** must match the uploaded GitHub Release asset exactly (wrong name → download 404).
- Recompute **`sha256`** whenever the APK bytes change.

---

## Repository layout

| File / area | Role |
|-------------|------|
| [`version.json`](./version.json) | OTA manifest (always on `main`) |
| [`changelog.md`](./changelog.md) | Human-readable release history |
| **[GitHub Releases](https://github.com/junaidshaik2600/life-os-releases-PUBLIC-/releases)** | APK files attached as download assets |

APK binaries are **not** stored in git — only on GitHub Releases.

---

## Release vs debug builds

| | Release | Debug |
|---|---------|--------|
| **For** | Users, OTA, GitHub Releases | Developer testing only |
| **Size** | ~75–80 MB | ~170–210 MB |
| **Signer** | Life OS | Android Debug |
| **In this repo** | Yes | Never |

---

## Security

- Download from **this repo’s Releases** or use the in-app updater.
- When `sha256` is set in `version.json`, the app can verify the APK after download.
- Prefer **release-signed** builds for anything you share or ship via OTA.

---

## Changelog

See **[changelog.md](./changelog.md)** for version history.

---

## Support

When reporting an issue, include:

- App version (**Settings → App info**)
- Whether you installed via OTA or manual APK
- The release tag (e.g. `v1.1.5`)

---

<p align="center">
  <strong>Life OS</strong> · Life Pulse on your device · your data stays local
</p>
