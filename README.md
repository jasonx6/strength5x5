# Strong 5×5 — Install Guide

This folder is a complete, standalone web app (a PWA). To get a home-screen
icon that launches independently, you put these files online once, then "Add
to Home Screen" from your phone.

## Files in this folder
- `index.html` — the whole app
- `manifest.webmanifest` — app name, icon, colors
- `sw.js` — service worker (makes the app work offline)
- `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` — app icons

Keep all files together in the same folder. Do not rename them.

---

## Step 1 — Put the folder online (pick ONE host)

A PWA must be served over **https** for "install" and offline to work.
Opening `index.html` directly from your phone's files will NOT work.

### Option A — Netlify Drop (easiest, ~1 minute, free)
1. On a computer, go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. It gives you a URL like `https://random-name-123.netlify.app`.
4. (Optional) Make a free account to rename it and keep it permanently.

### Option B — Cloudflare Pages (free)
1. Go to https://pages.cloudflare.com → "Create a project" → "Direct Upload".
2. Upload this folder. You get a `https://your-project.pages.dev` URL.

### Option C — GitHub Pages (free, if you use GitHub)
1. Create a new repository, upload all the files into it.
2. Repo → Settings → Pages → Source: "Deploy from branch" → `main` / root.
3. Wait ~1 minute. URL is `https://YOURNAME.github.io/REPONAME/`.

---

## Step 2 — Add it to your home screen

Open the URL from Step 1 in your phone browser, then:

### iPhone / iPad (use Safari)
1. Open the URL in **Safari** (not Chrome — only Safari can install PWAs on iOS).
2. Tap the **Share** button (square with an up arrow).
3. Scroll down → **Add to Home Screen** → **Add**.
4. The Strong 5×5 icon is now on your home screen. It opens full-screen,
   no browser bar.

### Android (Chrome)
1. Open the URL in **Chrome**.
2. You'll see an **"Install Strong 5×5"** bar inside the app — tap **Install**.
   (Or: Chrome menu ⋮ → **Install app** / **Add to Home screen**.)
3. The icon appears in your app drawer / home screen and runs like a normal app.

---

## Notes

- **Offline:** after the first load, the app works with no internet —
  open it on a plane, in a basement gym, anywhere.
- **Your data** (weights, history, progress) is saved on the device in the
  browser's local storage. It stays between sessions. It is NOT synced to the
  cloud and NOT shared between devices.
- **Backup:** since data is local, clearing your browser data or deleting the
  app will erase your history. There is an "Erase all data" button in Settings
  if you ever want a fresh start on purpose.
- **Updating the app later:** re-upload a new `index.html` to the same host.
  Bump the `CACHE` value in `sw.js` (e.g. `strong5x5-v6`) so the service
  worker fetches the new version instead of the cached one.
