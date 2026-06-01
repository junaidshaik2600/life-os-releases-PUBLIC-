> **Docs navigation**
> - **Full app flow (diagrams):** [APP-FLOW.md](../APP-FLOW.md)
> - **Documentation map:** [DOCUMENTATION-MAP.md](../DOCUMENTATION-MAP.md)
> - **Page / button / class / DB:** [page-reference/INDEX.md](../page-reference/INDEX.md)
> - **Master index:** [INDEX.md](../INDEX.md)

---

# Releases

Life OS uses **semantic versioning** (`MAJOR.MINOR.PATCH`). Human-readable notes live here; the app can optionally load a remote **version manifest** for update hints.

| File | Purpose |
|------|---------|
| `version-manifest.example.json` | Shape for hosted `version.json` (private HTTPS). |
| `TEMPLATE.md` | Copy per release under `vX.Y.Z.md`. |
| `v0.1.0.md` | Example completed release note. |
| `v0.4.0.md` | Premium billing + entitlements (Play Console checklist). |
| `v1.0.0.md` | Single-source versioning (`pubspec` + `AppVersion`). |

## Private repository + public APKs

- Keep **source** on a private GitHub (or equivalent) repo.
- Host **APKs and manifests** on separate storage (S3, private bucket, self-hosted HTTPS) referenced only by URL in the app config.
- Never commit signing keys or production manifest URLs with secrets.

## Wiring the app

1. Set `AppConfig.updateManifestUrl` to the HTTPS URL of your manifest JSON.
2. Keep `pubspec.yaml`’s `version:` line authoritative; the running app reads semver via `AppVersion` / `package_info_plus` (no second constant in Dart).
3. APK sideload UI: Settings → Check updates (`docs/13-app-updates-and-apk-sideload.md`).

See also: `docs/release-workflow.md`.

---

## Maintainer atlas

- **Living architecture book:** [../INDEX.md](../INDEX.md)
- **Photos & gallery:** [../11-image-picking-and-media.md](../11-image-picking-and-media.md)
