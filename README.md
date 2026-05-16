# Valet Auto Leasing — Prototype

A single-file, self-contained HTML prototype of the Valet Auto Leasing website.

This is the approval artifact — not the production site. It exists to show the
seven-page user flow to leadership before we commit to building the real Next.js
backend behind it.

## What's in the box

`index.html` (~226 KB) is the entire site. Open it in a browser, double-click
it, attach it to an email, or drop it on any static host. It works offline —
React, Tailwind, and the compiled app are all inlined. No CDN dependencies.

Routes (hash-based, so no server config needed):

- `#/` — Home
- `#/qualifier` — Six-question qualifier
- `#/match` — Match confirmation
- `#/deal-check` — Dealer-quote upload
- `#/deal-check-thanks` — Deal Check confirmation
- `#/refer` — Affiliate / partner landing
- `#/faq` — Full FAQ

## What it does

- Real form interactivity: qualifier validates each step, deal-check has a
  working drag-and-drop, affiliate signup persists to session storage
- Hash routing so URLs work over `file://` and any static host
- Sticky nav with persistent BECOME A PARTNER call-to-action
- Brand auto-enrollment messaging in three places (homepage section, full-width
  brass band on `/refer`, FAQ #16)

## What it doesn't do (yet — production will)

- No real backend. Form submissions go to session storage and routing only.
- No analytics or affiliate tracking pixel.
- No actual file upload or quote parsing.
- No email automation.

Those all belong to the Next.js production build, which is a separate effort
once this prototype is approved.

## Deploy

Vercel auto-detects this as a static project. Zero configuration. Push to
GitHub, import in Vercel, take the resulting URL.

## Rebuilding from source

The HTML is a build output — React (UMD) + Tailwind (compiled CSS) + a
compiled JSX bundle, all inlined. To regenerate, the build pipeline is:

1. `npx esbuild src/app.jsx --bundle --minify --jsx=transform --jsx-factory=React.createElement --jsx-fragment=React.Fragment --outfile=dist/app.js`
2. `npx @tailwindcss/cli -i src/input.css -o dist/styles.css --minify`
3. `node build.js` (assembles the three pieces plus React UMD into `index.html`)

Source is not committed to this repo — it lives in the prototype workspace.
Once production starts, the React components port directly into a Next.js app.

---

Valet Auto Leasing · A Division of All State Auto Leasing &amp; Finance
