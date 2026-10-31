# HR Connect – Android install wrapper

Apps Script pages cannot be installed as apps (no manifest). This folder is a tiny
installable shell that loads your Apps Script dashboard inside it. Host it anywhere
that serves static files over HTTPS – GitHub Pages is free and takes 5 minutes.

## 1. Configure
Open `index.html` and replace `PASTE_YOUR_APPS_SCRIPT_EXEC_URL_HERE` with your web-app URL
(the one ending in `/exec`, same as `WEBAPP_URL` in the Settings tab).

## 2. Host on GitHub Pages (free)
1. Create a free account at github.com → **New repository** → name it `hr-connect` → Public → Create.
2. **Add file → Upload files** → drag all six files from this folder → **Commit**.
3. Repository **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)` → Save.
4. After ~1 minute your app is live at `https://<your-username>.github.io/hr-connect/`.

## 3. Switch the personal links
In the Google Sheet, `Settings` → `WEBAPP_URL` → change it to `https://<your-username>.github.io/hr-connect/`
then run **HR Rotation → Assign serials / links**. Personal links become
`https://<your-username>.github.io/hr-connect/?t=TOKEN` – same token, new front door.
(The Apps Script URL keeps working too; existing iPhone users need not change anything.)

## 4. Candidate experience (Android)
Open the personal link in Chrome → an **Install HR Connect** bar appears → tap Install →
Zenbyte icon on the home screen, opens full-screen, no browser bar. The token is remembered,
so the icon alone is enough from then on. iPhone: Safari → Share → Add to Home Screen (as before).

## Files
`index.html` (Android + install), `ios.html` (iPhone entry – no manifest on purpose), `manifest.webmanifest`,
`sw.js`, three icons. **Put your /exec URL in BOTH `index.html` and `ios.html`.**

## iPhone note
Candidates must add to home screen **from their personal link** (the page that already shows
their list). The wrapper bakes the token into the home-screen app so it opens signed in.
Adding from the plain `…/hr-connect/` address (no `?t=`) gives an icon that asks for the link.

## Updating
The dashboard itself lives in Apps Script – update it there as usual; the wrapper never needs
to change. If you ever edit the wrapper files, bump `CACHE = 'hrc-shell-v2'` in `sw.js`.
