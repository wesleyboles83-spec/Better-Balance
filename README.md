# Better Balance V3

An iPhone-first, installable progressive web app for tracking alcohol spending, alcohol-free days, estimated savings credits, and financial goals.

## Features

- Log individual drinks (date, category, name, cost, location), edit or delete entries.
- Mark an alcohol-free day, recording its savings credit at that moment.
- Monthly and lifetime net balance = recorded savings credits minus drink costs.
- Goal name, amount, start date, target date, progress, and required weekly net improvement.
- Insights: average cost **per drinking day**, total spent, drinking days, alcohol-free days, average drinks per drinking day, previous-month comparison, daily spending chart.
- Optional suggestion to set *future* daily savings credits based on the selected month's average drinking-day spending.
- Local storage and JSON export/import. No accounts, trackers, or third-party dependencies.
- Offline support after first successful load via service worker.

## Install on iPhone (recommended: GitHub Pages)

A PWA needs a secure `https://` web address. Opening `index.html` directly from Files on your iPhone is **not** sufficient for reliable installation, storage, or offline use.

1. Unzip the package on a computer.
2. Sign in to https://github.com and create a new repository, e.g. `better-balance`. You can use a public repository for free GitHub Pages; note that **the source code** will be public, but personal records stay in your browser and are not uploaded to the repository.
3. In the repository, choose **Add file → Upload files**. Upload **the seven files inside** `better-balance-v3` (not the enclosing folder): `index.html`, `app.js`, `styles.css`, `sw.js`, `manifest.webmanifest`, `icon-192.png`, and `icon-512.png`. Commit the changes. You may also upload this README.
4. Open **Settings → Pages** in the GitHub repository. Under **Build and deployment**, select **Deploy from a branch**, choose `main` and `/ (root)`, then save.
5. Wait for the Pages site to be published. The address should resemble `https://YOUR-USERNAME.github.io/better-balance/`. GitHub shows the exact live URL in Settings → Pages.
6. Open that HTTPS address in **Safari on your iPhone**. Tap **Share → Add to Home Screen → Add** (on some iOS versions, the action is in the Share menu's More/Actions area).
7. Open Better Balance from the new Home Screen icon. Set a goal in **Home → Edit goal**, then log a drink or alcohol-free day.
8. Go to **Settings → Export JSON backup** regularly. Save backups to Files/iCloud Drive. To restore, use **Import a JSON backup**. Import replaces existing app data.

If your account/repository settings do not offer free Pages for private repositories, use a public repo or another static HTTPS host. **Do not upload any personal backup JSON files to GitHub.**

## Run locally on a computer

From the extracted directory:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000`. Localhost supports service workers in modern browsers. The app is static: no npm install or build step required.

## Data and privacy

Data is stored using browser `localStorage` for the origin where the app runs. Browser data clearing, private browsing, switching browsers, moving to a different web address, or device replacement can remove or isolate that data. iOS may evict website data in some circumstances. JSON export is the backup mechanism; there is **no cloud synchronization or encryption-at-rest provided by the app**. A person with access to the unlocked browser/device may be able to see entries. Do not use this as the sole copy of important data.

An alcohol-free day gets the credit in effect when it is logged. Updating the default credit or accepting the suggested credit does not recalculate old entries. Editing an old alcohol-free entry can change its individual credit.

The monthly comparison only compares months with recorded drinking days. Unlogged dates are never presumed to be alcohol-free. The goal's net progress can be negative; the visual progress bar is floored at zero, but the amount still needed includes any negative balance. Goal pace is a straight-line comparison to the target amount and date, not a forecast.

## Files

- `index.html`: document and PWA metadata
- `styles.css`: responsive iPhone layout
- `app.js`: app functionality and data storage
- `manifest.webmanifest`: app identity, install settings and icons
- `sw.js`: offline cache
- `icon-192.png`, `icon-512.png`: app icons

## Future public launch

Before inviting other users, add authentication, user-specific encrypted transport to a backend, reliable sync/backups, an accessible privacy policy, security review, and end-to-end testing on actual iOS devices. This release is a single-device personal-use MVP, not a multi-user production service.
