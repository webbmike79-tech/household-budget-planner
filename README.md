# Household Budget & Car Payoff Planner (PWA)

A self-contained, offline-first personal finance tool: monthly budget planning,
car payoff math, and a ZIP-code property-tax estimator, all in one HTML page.

## Hosting

This app is a static site — no build step, no server code. Drop the files on any
static HTTPS host and it works.

One easy option is GitHub Pages:

1. Create a public repo and push these files to the repo root.
2. In the repo: **Settings → Pages → Deploy from branch**, select `main` and `/ (root)`.
3. Your app will be live at `https://<username>.github.io/<repo>/`.

Any other static host works too (Netlify, Cloudflare Pages, a web server you run).

> **Important:** the offline service worker (`sw.js`) only registers on **HTTPS**
> or `localhost`. Over plain `http://` the app still runs, but offline caching is
> skipped silently.

## Installing

**On a phone (Android/Chrome):** open the hosted URL → menu → *Install app* /
*Add to Home screen*. It launches full-screen like a native app and works
offline after the first visit.

**On desktop (Chrome/Edge):** an install icon appears in the address bar —
click it to get a standalone window.

**iOS:** Safari → Share → *Add to Home Screen* (service workers do not apply,
but the app itself still runs).

You can also just open `index.html` directly from a local file — everything
except the service worker runs.

## Notes

- The **ZIP-code property-tax estimator** needs internet access: it looks up
  the ZIP at `https://api.zippopotam.us`. Everything else in the app is fully
  offline.
- Your budget numbers are stored only in your own browser (`localStorage`),
  optionally encrypted with a passphrase you choose.
