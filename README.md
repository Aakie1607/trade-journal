# VOID — Trade Journal

A Vite + React app, ready to deploy to Vercel.

## Run locally

```bash
npm install
npm run dev
```

## Deploy to Vercel

**Option A — via GitHub (recommended)**
1. Push this folder to a new GitHub repo.
2. Go to https://vercel.com/new and import that repo.
3. Vercel auto-detects Vite — leave the defaults (Build Command: `vite build`, Output Directory: `dist`) and click **Deploy**.
4. Every future push to the repo redeploys automatically.

**Option B — via Vercel CLI (no GitHub needed)**
```bash
npm install -g vercel
cd void-trade-app
vercel        # first deploy, follow the prompts
vercel --prod # promote to your production URL
```

## Data storage note

The app persists trades and settings using `window.storage`, an API originally
provided by the Claude Artifacts sandbox. `src/storage.js` polyfills that same
API using the browser's `localStorage`, so no code in `App.jsx` had to change.

This means data is **local to each browser/device** — there's no sync across
devices or backend database. If you want real persistence (e.g. shared across
devices, or a proper backend), swap the calls in `src/storage.js` for a real
API (e.g. Vercel KV, Supabase, Firebase) — the `get`/`set`/`delete`/`list`
call shape can stay the same.
