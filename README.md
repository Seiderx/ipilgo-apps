# ipilgo-apps

Public download site for the IpilGo Android apps (tourist + owner), plus the
Privacy Policy and Data Deletion pages required for Facebook login.
Static HTML, hosted on Render. The APK files are attached to GitHub Releases
of this repo, never committed.

| File | Purpose |
|---|---|
| `index.html` | Download page (buttons, QR codes, install steps) |
| `privacy.html`, `data-deletion.html` | Legal pages (linked from Meta / Google consent screens) |
| `version.json` | Latest version of each app; the apps read it to show "Update available" |

## Releasing a new version

1. In the app's `app.json`, raise `"version"` (e.g. `1.0.0` → `1.0.1`) **and**
   `android.versionCode` (e.g. `1` → `2`). Android refuses an update whose
   versionCode is not higher.
2. Build the release APK locally (signed with `credentials/release.keystore`).
3. Create a new GitHub Release in this repo (tag e.g. `v1.0.1`) and attach
   **both** files with exactly these names, so the "latest" links keep working:
   - `IpilGo-Tourist.apk`
   - `IpilGo-Owner.apk`

   If only one app changed, re-attach the unchanged APK from the previous release.
4. Update `version.json` with the new version number (and optional `notes`),
   commit, and push. Installed apps show the update prompt the next time they open.
   Set `"required": true` only when old versions must stop being used.
