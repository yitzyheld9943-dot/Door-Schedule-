# Door Schedule Builder — Web App (open it on your tablet)

This is a hosted version. Once you deploy it (about 10 minutes, one time), you get a web link you can open in Chrome on your **Android tablet, phone, or any computer** — no install needed. You can even "Add to Home screen" so it feels like an app.

---

## What you'll do (overview)
1. Make a free GitHub account and put these files there.
2. Connect GitHub to a free Vercel account.
3. Paste your Anthropic API key into Vercel once.
4. Get your link. Open it on your tablet. Done.

You only do steps 1–3 once. After that you just open the link.

---

## Step 1 — Get your Anthropic API key
1. Go to **https://console.anthropic.com/settings/keys**
2. Sign in (or create an account), click **Create Key**, copy the key (starts with `sk-ant-`).
3. Keep it somewhere for a minute — you'll paste it in Step 3.

---

## Step 2 — Put the files on GitHub
1. Go to **https://github.com** and make a free account if you don't have one.
2. Click the **+** (top right) → **New repository**.
3. Name it `door-schedule` , leave it Private, click **Create repository**.
4. On the next page click **uploading an existing file**.
5. Drag in **everything inside this folder** (the `api` folder, the `public` folder, `vercel.json`, `package.json`). Keep the folder structure.
6. Click **Commit changes**.

> Tip: the structure must stay as:
> ```
> api/read.js
> public/index.html
> public/app.js
> public/pdf-lib.min.js
> public/icon.png
> public/manifest.json
> vercel.json
> package.json
> ```

---

## Step 3 — Deploy on Vercel + add your key
1. Go to **https://vercel.com** → **Sign up** → choose **Continue with GitHub**.
2. Click **Add New… → Project**.
3. Find your `door-schedule` repo and click **Import**.
4. **Before clicking Deploy**, open the **Environment Variables** section and add:
   - **Name:** `ANTHROPIC_API_KEY`  **Value:** *(paste your sk-ant-… key)*
   - *(optional, recommended)* **Name:** `APP_PASSWORD`  **Value:** *(any password you choose — keeps strangers from using your key if they find the link)*
5. Click **Deploy**. Wait ~1 minute.
6. You'll get a link like `https://door-schedule-xxxx.vercel.app`. That's your app.

---

## Step 4 — Open it on your tablet
1. Open **Chrome** on your Android tablet, go to your Vercel link.
2. *(If you set APP_PASSWORD:)* the first time, open the link with `#` then run this once in the browser — actually simpler: just tap the **⋮ menu → Add to Home screen** to keep it handy. For the password, see the note below.
3. Tap the three sources, pick your PDFs, tap **Read plans**.

### If you set an APP_PASSWORD
The app needs to know the password. Easiest way: open the link on the tablet, then in Chrome's address bar type:
```
javascript:localStorage.setItem('dsb_pw','YOUR_PASSWORD');location.reload()
```
(Chrome may strip the `javascript:` — if so, just don't set APP_PASSWORD; keeping the link private is usually enough for personal use.)

**Simplest path for just-you use:** skip APP_PASSWORD entirely in Step 3. Your link is private and unlisted; only you have it.

---

## Using it day to day
- Add up to three PDFs (floor plans, enlarged unit plans, wall sections + door schedule). You can add just the sheets you need.
- Type page numbers (e.g. `49-52`) to read only those pages — faster and cheaper.
- Tap **Read plans & build schedule**.
- Review the schedule grouped by unit; tap any cell to fix it.
- **Save** (kept on that device), **Copy** to paste into Excel, or **Export CSV**.

## Good to know
- **Your key lives only in Vercel**, never in the browser — safe to use on the tablet.
- **Cost:** a few cents per run for a few sheets. Use the page boxes to keep it small.
- **Accuracy:** reading drawings is hard for AI; always eyeball the result. Every cell is editable.
- **Saved projects** are stored per-device (in the browser), so a project saved on the tablet shows on the tablet.

## Updating later
Change a file on GitHub (or re-upload) and Vercel redeploys automatically in about a minute.
