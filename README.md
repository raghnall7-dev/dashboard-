# Simple Money

A beginner-friendly money app that runs in the browser. Buyers enter their pay, bills and goals once. After that they tap **+** when they spend something, and the app tells them what's safe to spend this week. A built-in **Money Coach** gives plain-English tips.

- No account, no subscription, no bank connection. Data stays on the buyer's device.
- Works on phones (can be added to the home screen like an app), tablets and computers.
- Works offline.
- Light and dark mode, 6 accent colours, £ / $ / € / CA$ / AU$.

## What's inside

| Screen | What it does |
|---|---|
| **Setup** | 4 quick questions: name, pay, bills, first goal. Ends with "You can safely spend £X a week". |
| **Home** | Safe-to-spend this week, a top Coach tip, this week's chart, the month split (needs / treats / savings), coming-up bills and paydays, goals, recent spending. |
| **Add (+)** | Amount, a category, done. Money in and money out. Today / yesterday / pick a date. |
| **Spending** | Month by month: total, per-day average, where it went, every entry (tap one to edit or delete). |
| **Goals** | Progress bars, "on track" or "running late" (with the monthly amount that fixes it), add or take out money. |
| **Coach** | "Your money, explained" in plain words, the top 3 next steps, a 50/30/20 check, all tips. |
| **Settings** | Name, pay, bills, your own categories, look, currency, backup / restore, example data, delete everything. |

The Money Coach is a set of rules inside the app. It is not an AI service, so it costs nothing to run, works offline and never sends data anywhere. Don't describe it as "AI" in listings.

## Files

| File | Purpose |
|---|---|
| `index.html` | The whole app. This one file also works on its own as the offline version. |
| `manifest.webmanifest`, `sw.js` | Let the hosted version install on a home screen and work offline. |
| `icon.svg`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png` | App icons. |

## Try it locally

Open `index.html` in a browser. Or, for the full app experience (install and offline):

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

On the first screen, tap **"Just look around with example data"** to see it filled in.

## Making niche versions (student, mum, couples…)

Everything that changes between versions is in the `CONFIG` block at the top of the script in `index.html`:

- `appName`, `tagline`
- `categories` (each one is a `need` or a `want`, which drives the needs / treats split)
- `billSuggestions` and `goalSuggestions` shown during setup
- `incomeTypes` for "money in"

Change the default accent colour in `freshState()` (`accent: 'indigo'`). Then update the name in `manifest.webmanifest` and the `<title>` / `apple-mobile-web-app-title` tags in `index.html`.

## Hosting the online version

The app is static files, so any static host works. Options:

1. **GitHub Pages:** repo **Settings → Pages → Deploy from a branch → `main` / root**. On a free GitHub plan the repo has to be **public**, which means anyone could see and copy the code.
2. **Netlify or Cloudflare Pages:** free, and they can deploy from a **private** repo. Netlify also lets you drag and drop the folder at app.netlify.com/drop.

After publishing changes, bump `VERSION` in `sw.js` so installed copies pick up the update.

## Delivering it on Etsy

Etsy digital listings deliver files, so the usual set-up is:

1. A **PDF** with the link to the hosted app, a QR code for phones, and a short picture guide ("Add to Home Screen").
2. The **`index.html`** file as the offline copy (renamed to something like `Simple-Money-Offline.html`).

Anyone with the link can open the hosted version. That's normal for this kind of product. You can change the link later if it gets shared around.

## Data and privacy

Everything is saved in the browser's local storage on that device. The hosted version and the offline file keep separate data. **Download a backup** and **Load a backup** in Settings move data between devices.
