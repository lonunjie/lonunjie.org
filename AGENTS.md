# lonunjie.org Agent Instructions

Public website for https://lonunjie.org/, nested in the SeedLife control plane
(`~/dig/lonunjie`, repo `lonunjie/hq`). **Read `../AGENTS.md` first** —
org-wide rules, the registry, and the one shared memory (`../memory/`)
live there. This repo has no memory of its own.

## How it deploys

- Cloudflare Pages project `lonunjie`, git-connected to this repo.
  **Push to `main` = production deploy.** Any other branch gets a
  preview URL (`<hash>.lonunjie.pages.dev`, marked noindex).
- No build step. Pages serves `public/` only — everything outside it
  (this file, README, LICENSE) is never published.
- Cadence: **smart batched deploy** — commit as you go, review on a
  preview branch, push `main` once the operator approves visible changes.

## Site rules

- Plain HTML/CSS, **no JavaScript, no third-party requests, no web
  fonts.** `public/_headers` enforces this with a strict CSP; widen it
  deliberately or not at all.
- Works in light and dark (`prefers-color-scheme`), at 375px with no
  horizontal scroll, and with reduced motion.
- **Keep `public/assets/bimi/lonunjie.svg` at that exact path** — the BIMI DNS
  record (`../infra/dns.tf`) points mail clients at it. Also keep
  `public/images/*` paths stable; old share cards and profiles link them.
- `public/_redirects` holds short links (e.g. `/cometpro`).
- This is a PUBLIC repo — no private notes, plans, or credentials here.
