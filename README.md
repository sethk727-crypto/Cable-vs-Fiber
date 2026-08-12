# Cable vs Fiber — The Doorstep Demo

An animated, mobile-first comparison of **Brightspeed Fiber vs Spectrum (cable)**
built as a **door-to-door sales aid**: a single HTML page a rep opens on a phone
at the doorstep. The rep talks; the visual proves.

## What's in here

| File | What it is |
|---|---|
| `index.html` | The demo itself — one self-contained file, zero dependencies, works offline |
| `capacity.html` | Standalone full-screen **Network Capacity Comparison** — the live topology simulator as its own app-style screen (linked from the demo's simulator card, ✕ returns to the demo) |
| `neighborhood.html` | **Neighborhood Grid Simulator** — homeowner-facing street map built for ages 46–75+: big type, ≥54px touch targets, zero jargon. Tappable neighbor houses, a 12 PM–10 PM time slider, a "make all the neighbors stream" toggle, a live speed gauge, and a peak-hour value calculator ("$36 of $120") |
| `diagnostic.html` | **Infrastructure Node Diagnostic** — an iOS-styled, tech-tool-feel *simulation* (persistently badged as such): search bar + authority-cadence loading, hazard dashboard of a typical shared node (pulsing red trunk split, ≈47 devices typical, 4% upload ratio, 28% peak delivery, $-waste calculator), and a big iOS switch that transitions the whole UI to the dedicated-fiber state |
| `manifest.json` + `sw.js` | PWA layer — after one online visit the whole site works offline and can be saved to a phone/iPad home screen |
| `prompts/d2d-visual-master-prompt.md` | The master system prompt (SaaS conversion architecture adapted for d2d visuals) used to design this page — paste into Claude to generate variants for other markets/providers |
| `vercel.json` | Zero-build static deploy config |

## Fiber brand switcher (Brightspeed / T-Mobile Fiber)

Both pages support a **fiber brand**: `Brightspeed Fiber` (amber) or
`T-Mobile Fiber` (magenta `#E20074` — validated colorblind-safe against
Spectrum blue, worst-pair CVD ΔE 19.3). Switching the brand restyles marks,
accents, the CTA, and all wording (legends, race lanes, table headers, SMS
text).

- On `capacity.html`: use the **Fiber Brand** stepper.
- Anywhere: deep-link with `?brand=tmobile` or `?brand=brightspeed`.
- The choice persists on the device (localStorage) and is shared between the
  demo and the capacity page.

## The capacity page

`capacity.html` mirrors the reference "Network Capacity Comparison" screen and
goes further: live particle physics, **Both** mode (star and bus running side
by side), Connection Type / Time of Day / Fiber Brand steppers, live-wobbling
STATUS · LATENCY · PER HOME telemetry, an **Auto demo** that plays the reveal
arc (fiber calm → cable calm → cable jam → both), a Share button
(native share sheet or copy-link), and shareable URL state
(`?brand=…&conn=…&tod=…`).

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

## The neighborhood page

`neighborhood.html` is the homeowner-facing section: an animated street where
one **Shared Cable Pipe** serves six homes (yours is the highlighted one at the
end of the line) versus a **Dedicated Fiber Highway** per home. Sliding the
time-of-day past 5 PM wakes the neighbors' TVs, the pipe glows red, packets
stutter and pile up, and the speed gauge drops — while fiber stays locked at
100%. Green/red are used as status signals only and always carry a word or
icon ("✅ Full speed" / "🚧 Evening Bottleneck"), and the fiber data pulses are
cyan, which stays distinguishable from red under red-green color-blindness
(validated: cyan↔red CVD ΔE 22.8). The value calculator turns the dip into
dollars: pick the bill, see what peak hours actually deliver.

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
