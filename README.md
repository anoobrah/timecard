# Daily Timecard

A personal time tracker that installs on your phone like an app. It has:

- a start/stop clock
- manual entries for time you forgot to track
- totals by activity
- a day-by-day time card

It works offline and needs no account. All data stays in the browser on the device where you use it.

## Files

| File | What it does |
|---|---|
| `index.html` | The whole app (layout, styles, logic) |
| `manifest.webmanifest` | Name, icon and colors the phone uses when installing |
| `sw.js` | Service worker that caches the app so it opens offline |
| `icons/` | App icons (normal, maskable for Android, Apple touch icon) |

## Put it online with GitHub Pages (free, about 5 minutes)

To install as an app, it has to be served over HTTPS. GitHub Pages does that.

1. Create a new **public** repository on GitHub, for example `timecard`.
2. Upload everything in this folder, keeping the `icons` folder.
   - From a terminal:
     ```bash
     cd timecard-app
     git init
     git add .
     git commit -m "Daily Timecard"
     git branch -M main
     git remote add origin https://github.com/<your-username>/timecard.git
     git push -u origin main
     ```
   - Or use **Add file → Upload files** on the repo page.
3. In the repo, open **Settings → Pages**.
   - Under **Build and deployment**, set Source to **Deploy from a branch**.
   - Pick branch `main` and folder `/ (root)`, then click **Save**.
4. After a minute or so, the site is live at `https://<your-username>.github.io/timecard/`.

## Install it on your phone

1. Open that address in **Chrome** on your phone (Samsung Internet also works).
2. Tap the menu (⋮), then **Install app** (on some versions it's **Add to Home screen → Install**).
3. Timecard gets its own icon and opens full screen.
4. After the first open, it works without internet.

On iPad or iPhone: open the address in Safari, tap **Share**, then **Add to Home Screen**.

You can also install it on your Ubuntu laptop. Open the address in Chrome and click the install icon at the right end of the address bar. Each device keeps its own separate data.

## Your data

- Entries are stored in this browser's local storage, on this device only.
- Uninstalling the app or clearing Chrome's site data for the address **deletes your log**.
- Tap **Back up** now and then, and keep the `.json` file somewhere safe, such as Google Drive.
- **Restore** merges a backup into the current log. Existing entries are kept, so restoring twice won't create duplicates.
- **Export CSV** gives the selected range as a spreadsheet file.

## Updating the app

Edit the files, then commit and push. The app picks up the new version the next time it opens while online.

If you change `sw.js`, also bump `CACHE = "timecard-v1"` to `v2`, so old cached files get replaced.

## Ideas for later

To sync between phone and laptop, add a small backend. For example:

- FastAPI + SQLite with endpoints such as `GET/POST /entries`.
- Change `saveLocal()` / `loadLocal()` to call that API.

It's a good portfolio project.
