# Cable vs Fiber — The Doorstep Demo

An animated, mobile-first comparison of **Brightspeed Fiber vs Spectrum (cable)**
built as a **door-to-door sales aid**: a single HTML page a rep opens on a phone
at the doorstep. The rep talks; the visual proves.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The demo itself — one self-contained file, zero dependencies, works offline |
| `prompts/d2d-visual-master-prompt.md` | The master system prompt (SaaS conversion architecture adapted for d2d visuals) used to design this page — paste into Claude to generate variants for other markets/providers |

## The demo, in 90 seconds

1. **Understand** — auto-playing *upload race*: the same 2 GB video sent on both
   networks, with real computed times (sped-up playback, honest clocks) and a
   `30×` hero stat. Tap **Replay** for the dramatic beat.
2. **Evaluate** — a bento of animated proof cards: the **7 o'clock slowdown**
   (shared-node congestion curve), the **lag test** (ping animation), the
   **live capacity simulator** (below), the **24-month bill** (promo step-up
   chart with 2-year totals), and a **scenario picker** that converts speeds
   into "back up 5,000 photos" time.

### The capacity simulator

A canvas particle simulation of one street with five homes, in the style of a
network-topology explorer: **fiber as a dedicated star** (one strand per home,
orderly packets, both directions equally fast) vs **cable as a shared bus**
(one trunk split at a node — packets jitter and queue on the trunk, upstream
dots crawl). Steppers switch **Connection** (Fiber / Cable / Both, side by
side) and **Time of day** (Morning / Afternoon / Evening Peak); packet speed,
spawn rate, status, latency, and per-home delivered speed react live — step
Evening Peak and watch the cable trunk jam while fiber doesn't move. The
animation pauses off-screen and honors reduced motion.
3. **Trust** — a straight side-by-side table that concedes the ties (no
   contract, no data cap on both) so the upload row lands harder.
4. **Decide** — sticky dual-intent CTAs: *See if my address has fiber* (30-second
   quick win) and *Text me this* (pre-filled SMS so the pitch survives the door
   closing).

**Pitch mode** (toggle, top-right): reveals rep-only talk tracks, discovery
questions, and objection counters under each section, plus a floating
**guided pitch bar** — ‹ › steps that walk the seven beats of the pitch in
order (hook → 7 pm story → live simulator → lag test → price truth → concede
the ties → close), auto-scrolling to each card and re-firing its animation
live so every proof plays fresh in front of the customer. The setting persists
on the rep's phone.

## Make it yours

Every number a prospect sees lives in the `CONFIG` object at the top of the
`<script>` in `index.html` — plan names, speeds, latency, promo/post-promo
pricing, promo length, scenario list, CTA link, and SMS text. Edit it for your
market; everything downstream (race clocks, charts, totals, table) recomputes.

Open `index.html` directly in any browser, or deploy it (below) and save it to
the rep's phone home screen — it ships a home-screen icon and app-style meta
tags, and runs fully offline once loaded.

## Deploying on Vercel

The repo is a zero-build static site: `vercel.json` is included, `index.html`
is the only entry point, and there are no dependencies or build step — import
the repo into Vercel and it deploys as-is.

- Every push to a branch gets an automatic **preview URL**; production deploys
  from the project's production branch (usually `main`), so merge this branch
  to go live.
- After deploying, paste your live URL into `CONFIG.ctas.smsBody` so the
  **Text me this** button delivers the page to the customer's phone, and point
  `CONFIG.ctas.checkUrl` at your real availability/order link.

## Design notes

- Two-series identity is fixed page-wide — fiber amber `#c98500`, cable blue
  `#3987e5` — validated for colorblind safety and contrast on the dark surface
  (worst-pair CVD ΔE 27.4, far above the ≥8 target). Identity is never
  color-alone: legends, labels, and position everywhere.
- One axis per chart, no truncated scales, thin marks, hairline grids.
- Animations are labeled sped-up illustrations; clocks and totals show real
  computed values, with a one-tap "show the math" breakdown. The congestion
  curve is labeled illustrative. Full `prefers-reduced-motion` fallbacks.

## Disclaimer

Example plans, speeds, and prices for illustration only — offers vary by
address and change over time; verify current offers before quoting. This is a
sales aid built on the fiber side of the conversation, **not** an official
Brightspeed or Charter/Spectrum property. Spectrum is a trademark of Charter
Communications; Brightspeed is a trademark of Connect Holding LLC.
