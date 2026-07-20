# KinneHo? Nepal — LED Motorcycle Projector Turn Signal Lights

Single-page landing site for the **KinneHo? Nepal** Facebook page, selling LED
motorcycle turn signal lights with a ground projector (arrow / yellow light),
27 RGB modes, and IP67 waterproofing. The site is also used as the **Meta app
website URL** for the Facebook automation app.

## Live Site
- **URL:** https://shivramsaud.github.io/kinneho-nepal/
- **Repo:** https://github.com/shivramsaud/kinneho-nepal (public)
- **Hosting:** GitHub Pages (master branch, root `/`)

## Business
- **FB Page:** https://www.facebook.com/profile.php?id=61592100261714
- **FB Messenger:** https://www.facebook.com/messages/t/61592100261714
- **WhatsApp:** +9779841852585 → https://wa.me/9779841852585
- **Product:** LED Motorcycle Turn Signal Lights with Projector
  - 9 Amber + 10 RGB LEDs per bulb, 6.6W–9.5W, 12V, M8 mount
  - 27 RGB modes, IP67 waterproof, ground arrow / yellow projection
- **Pricing:** NPR 2,500 / pair (single) · NPR 2,000 / pair (bulk, min 10 pairs)
- **Delivery:** Kathmandu 1–2 days, nationwide 3–5 days, COD available

## Local Preview
```
python -m http.server 8000
# open http://localhost:8000
```
(Serve from the repo root — `index.html` lives at the root, not in a subfolder.)

## Repository Layout
```
index.html          # Landing page (single file, inline CSS + JS)
images/             # logo.svg, logo-wordmark.svg, projection photos, videos
README.md
AGENTS.md           # Project context for AI agents
.gitignore
```

## Deploy Changes
```
git add -A
git commit -m "describe change"
git push origin master
# GitHub Pages rebuilds automatically (~30–60s)
```

## Roadmap
- Build the LangGraph automation agents (content / posting / response /
  analytics / scheduler) to auto-run the FB page.
- Fetch & store a real long-lived Facebook Page token.
- Optionally add a custom domain.
