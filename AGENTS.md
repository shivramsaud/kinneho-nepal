# AGENTS.md — KinneHo? Nepal Automation Project

Guidance for AI agents (and humans) working on this repository.

## Project Goal
Build a **LangGraph multi-agent system** that automates the Facebook page
**"KinneHo? Nepal"** (page ID `61592100261714`), which sells LED motorcycle
projector turn signal lights in Nepal. The system should:
- Generate marketing content (text + image selection) for posts.
- Publish posts to Facebook (manual + scheduled).
- Auto-respond to comments/messages.
- Track basic analytics.
- Run on a schedule.

A free single-page landing site (this repo) is used as the **Meta app website URL**.

## Business Facts (source of truth)
- **Brand / page name:** KinneHo? Nepal
- **FB Page ID:** `61592100261714`
- **FB Page URL:** https://www.facebook.com/profile.php?id=61592100261714
- **FB Messenger URL:** https://www.facebook.com/messages/t/61592100261714
- **WhatsApp:** +9779841852585 → https://wa.me/9779841852585
- **Product:** LED Motorcycle Turn Signal Lights with Projector
  - 9 Amber + 10 RGB LEDs per bulb
  - 27 RGB modes
  - IP67 waterproof
  - 6.6W–9.5W per bulb, 12V, M8 mount
  - Ground projection: arrow / yellow light
- **Pricing:**
  - NPR 2,500 / pair (single order)
  - NPR 2,000 / pair (bulk, minimum 10 pairs)
- **Delivery:** Kathmandu 1–2 days, nationwide 3–5 days, COD available.

## Tech Decisions
- **Free LLM:** OpenRouter (`openrouter/free`) or Groq (`llama-3.3-70b-versatile`).
- **Hosting:** GitHub Pages (this repo, `master` branch, root `/`).
  - Live URL: https://shivramsaud.github.io/kinneho-nepal/
  - This URL is the Meta app website URL.
- **Repo:** https://github.com/shivramsaud/kinneho-nepal (public).
- **Local preview:** `cd landing-page` then `python -m http.server 8000`
  (NOTE: site files were moved to repo root; preview from repo root now).

## Repository Layout
```
index.html            # The landing page (single file, inline CSS + JS)
images/               # All site assets (jpg/png/mp4/svg)
  logo.svg            # Badge favicon
  logo-wordmark.svg   # Nav + footer wordmark (icon + "KinneHo? Nepal")
  arrow-projection.jpeg, road-projection.jpeg, rear-projection.jpeg
  modes-27.jpeg, warning-mode.jpeg, brake-flash.jpeg, led-closeup.jpeg
  premium-build.jpeg, installation.jpeg, hero-bg.jpeg
  product-photo.jpeg, welcome-banner.jpeg   # legacy, not used in UI
  video-demo.mp4, video-night.mp4
README.md
AGENTS.md
.gitignore
```
Legacy/unused assets kept in repo but not referenced by the UI:
`logo.jpeg`, `product-photo.jpeg`, `welcome-banner.jpeg`, `hero-bg.jpeg`.

## Landing Page Design Notes
- Dark theme, glassmorphism, gradient accents (cyan `#00b4ff` → violet `#7c3aed`).
- Hero background uses `arrow-projection.jpeg` (shows projected arrow on ground).
- Final CTA background uses `road-projection.jpeg`.
- Logo is a generated SVG (projector headlight emitting a ground arrow).
  The user's intended WhatsApp logo image failed to attach — if provided,
  swap `images/logo-wordmark.svg` / `images/logo.svg` for it.
- Gallery + lightbox curated to projection-focused images only.
- Sections: hero, features, showcase rows, gallery, benefits, specs,
  pricing, FAQ, final CTA, footer.
- JS features: scroll reveal, sticky nav, countdown timer (7-day, localStorage),
  hero particle canvas, lightbox, smooth scroll.

## Facebook / Meta Setup Status
- Business portfolio created; Facebook Login product added to the app.
- **Long-lived Page access token:** NOT yet fetched (pending real token).
- App website URL: using the GitHub Pages URL above (placeholder resolved).
- Posting strategy (2025–2026 algorithm): Reels < 90s perform best;
  post in Nepal off-peak hours for reach.

## LangGraph Agent Architecture (planned, NOT yet built)
Intended agents (to be implemented under an `agents/` or `src/` dir):
1. **Content Agent** — writes post copy, picks best images/videos.
2. **Posting Agent** — publishes to FB Graph API (feed / video_reels).
3. **Response Agent** — replies to comments & Messenger messages.
4. **Analytics Agent** — pulls reach/engagement, summarizes.
5. **Scheduler Agent** — cron-like trigger for posting & analytics.
Orchestrator: LangGraph `StateGraph` with shared state.

## Conventions
- Keep the landing page a single self-contained `index.html` (inline CSS/JS)
  unless asked otherwise.
- Never commit secrets/tokens. Long-lived Page token must live in env vars
  or a secrets manager, never in the repo.
- Prefer free LLM tiers (OpenRouter/Groq) for the automation agents.
- Do NOT add code comments unless explicitly requested.

## How to Deploy Changes
```
git add -A
git commit -m "describe change"
git push origin master
# GitHub Pages rebuilds automatically (~30–60s)
```

## Open Items / Blockers
- Fetch & store a real long-lived Facebook Page token.
- Confirm final logo (SVG vs user-provided image).
- Build the LangGraph automation agents.
- Optionally add a custom domain to GitHub Pages.
