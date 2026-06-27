# Inspiration — Deep Analysis (per-site dossier)

> **What this is.** An exhaustive, corner-by-corner study of every reference site for the Tadfuq
> Al-Khayr design system. For each site: the **exact design tokens pulled from its live stylesheets**
> (colors, fonts, type sizes, radii, shadows, gradients, easings, `@keyframes`, backdrop-filters),
> the **page structure** (every section/heading/control, incl. below-the-fold), the **creative
> devices**, and **what we adopt**. Companion to `../design.md` (the system) — this file is the *evidence*.
>
> **Method & honesty.** Tokens were extracted directly from each site's HTML + CSS bundles
> (`_tokens.json`); content outlines from the server-rendered DOM (`_outline.json`); hero images via
> server-side render (`*.jpg`, `full/` attempts). Two honest limits: (1) the sandbox browser couldn't
> initialise system NSS, and the render service **caps screenshot height**, so we have *hero* images +
> *full token/DOM* extraction rather than full-page images; (2) SPA shells (designmd.me/.supply, parts
> of aura/neuform) inline their tokens in JS bundles, so their palettes below are partial. *Values are
> observed facts; commentary is paraphrased — content rephrased for compliance with licensing restrictions.*

---

## 1 · kinetics.colorion.co — "motion that has weight"

**Identity.** Dark warm-charcoal lab, a single **amber** accent, monospace instrumentation. The most
directly useful site for our motion layer.

**Exact tokens (from CSS)**
- **Palette (named vars):** `--graphite #0e0e10` · `--graphite-2 #141417` · `--card #1a1a1d` ·
  `--card-2 #232326` · `--line #2a2a2e` · text `--bone #ede9e0` / `--bone-dim #a8a6a0` /
  `--bone-faint #6e6c68` · accent `--amber #ff8a00` / `--amber-deep #b36200` · `--wire #5b8def` ·
  `--danger #ff5c5c` · `--ok #4cd08a`.
- **Fonts:** `Archivo` (display) · `JetBrains Mono` (mono/labels) · `Inter` (body).
- **Type sizes:** mono labels dominate at 11–14px; display up to 68px. Tracking `-0.02em` display, `+0.03–0.05em` mono caps.
- **Radii:** `50%`, `100px` (pills), plus an organic **blob radius `42% 58% 70% 30% / 45% 45% 55% 55%`**.
- **Shadows:** amber glow `0 0 48px 8px rgba(255,138,0,0.55)` and `0 0 20px rgba(255,138,0,0.35)`; hard offset `0 6px 0 #B36200`.
- **Easings:** spring/overshoot `cubic-bezier(0.34,1.56,0.64,1)`; entrance `cubic-bezier(0.16,1,0.3,1)`; in-out `cubic-bezier(0.65,0,0.35,1)`; soft `cubic-bezier(0.18,1.25,0.4,1)`.
- **Backdrop:** `blur(14px)`, `blur(6px)`.
- **`@keyframes` (45 total):** `spin · shimmer-sweep · ripple-out · marquee-scroll · pulse-ring · shake-x · confetti-fly · dot-wave · breathe · float-bob · blob-morph · neon-pulse · eq-pump …`

**Page structure.** H1 "Motion that has weight." → sections **Interaction & Input · Feedback & State ·
Surface & Motion** → "**Two numbers, not a duration.**" (the spring philosophy) → "**Built for the
copy-paste workflow.**". Every demo card ships **CSS / React / Prompt** tabs + **Copy**; live demos
(Hover near me, Trigger, Press anywhere, Hold, a 128 counter, ★). Accordions: "Why springs / Performance".

**Creative devices.** Single-accent + glow; mono "live readout" panel (`damping 24 · stiffness 320 · mass 1.0`);
the accent word coloured in the headline; tri-tab code/preview/prompt.

**Adopt → Tadfuq.** Confirms our motion tokens (entrance `cubic-bezier(.16,1,.3,1)`); use the **mono
live-readout** for any tunable/aggregate; **clamp** their `1.56` overshoot to ≤6% for our work UI.
Their amber is *their* signature — we keep indigo/gold; we borrow the *grammar*, not the hue.

---

## 2 · gradientbuttons.colorion.co — tonal button gallery

**Exact tokens.** Tailwind v4 (`color-mix(in oklab,…)`). Neutrals: `#0f172a · #334155 · #cbd5e1 ·
#f8fafc · #e2e8f0` (slate). Card **radius `10px`** dominant. Glow shadow `0 0 20px #eee`.
**Gradients are 2–3 stop, position-animated** — e.g. *Sea Blue/Nimvelo* `linear-gradient(to right,#2b5876
0%,#4e4376 51%,#2b5876 100%)`, *Horizon* `#314755 → #26a0da 51% → #314755`. Easing `cubic-bezier(.4,0,.2,1)`.
The hover trick: animate **`background-position`** across a 200%-wide gradient (51% midpoint), not the hue.

**Page structure.** 24 named swatches (Sea Blue · Nimvelo · Hazel · Noon to Dusk · YouTube · Cool Brown ·
Harmonic Energy · Playing with Reds · Sunny Days · Green Beach · Intuitive Purple · Emerald Water · Lemon
Twist · Monte Carlo · Horizon · Rose Water · Frozen · Mango Pulp · Bloody Mary…). Each card: title +
heart/copy + "HOVER ME" preview + **Show code / Copy CSS**.

**Adopt → Tadfuq.** Validates our **primary-CTA tonal gradient + position-shift hover** (use the navy
family `#2b5876→#4e4376`-style on our indigo). Card anatomy (title · actions · preview · footer-actions)
feeds our service-card and the gradient-button doc example.

---

## 3 · coverflow.ashishgogula.in — iOS cover flow for React

**Exact tokens.** shadcn (`hsl(var(--…))`). **Radii:** `9999px` pills, `32px`, `var(--radius)`, `calc(var(--radius) - 2px)`.
Easing `cubic-bezier(.4,0,.2,1)` (9×). `@keyframes enter · exit`. Tracking **`-0.025em`** on display.
Active scale `0.98`. Dot-grid bg `radial-gradient(#ffffff59 1px,#0000 0)`. Glass `inset 0 1px #ffffff0d` + `blur(10px)`.

**Page structure.** H2 "iOS-like Cover Flow for React." → feature trio **Fluid Physics Engine ·
Keyboard First · Zero Layout Shift · Touch Ready · Dark Mode Native**; a "Midnight Dreams" demo album;
a mono `npx shadcn add …coverflow.json` install bar.

**Creative devices.** Crosshair `+` corner marks framing the hero (draughtsman); mono install bar w/ copy;
GitHub-star + theme toggle in nav.

**Adopt → Tadfuq.** Our **Cover-Flow services showcase** (§6.8) — keep "zero layout shift via isolated
transforms" + keyboard-first; the **crosshair framing** as an optional hero device; active-press `scale .98`.

---

## 4 · backgrounds.supply — gradient/texture library (Framer)

**Exact tokens.** Fonts `Inter / Inter Display / Satoshi / Geist`. Canvas near-black-blue `rgb(3,6,17)`;
accents `#09f (rgb 0,153,255)` blue + `rgb(255,60,113)` pink. Radii `12 · 16 · 32px`, `50%`.
**Backdrop `blur(12px)` & `blur(22px)`.** Shadow `0px 12px 40px rgba(0,0,0,0.45)`. Tracking **`-0.02em`** (182×).
Signature **edge-fade mask** `linear-gradient(to right, transparent, #000 12.5%, #000 87.5%, transparent)`
for marquees; border `#ffffff1a`. Easing `cubic-bezier(.44,0,.56,1)`.

**Page structure.** H1 "Jaw-dropping backgrounds…" → "29 Collections · 1,273 Backgrounds · Use for lifetime"
→ Gradient Lab → FAQ (10 Q). Nav: Usecases · Discover · Pricing · Freebies · Blog · Gradient Lab.

**Creative devices.** Black starfield + **single glossy 3D pink asterisk** (one lit object); **serif-italic
emphasis word**; white primary pill + dark secondary; edge-fade marquee masks.

**Adopt → Tadfuq.** The **edge-fade mask** for any horizontal scroller/ticker; backdrop `blur 12–22px`
defaults; "one lit 3D-spot object" hero; serif-italic emphasis (already sanctioned).

---

## 5 · styles.refero.design — DESIGN.md examples gallery

**Exact tokens.** Fonts **`Neue Montreal`** (display) + `JetBrains Mono`. Light `#f7f8fb` / dark `#0d0f15`;
ink `#000 / #171717`; muted `#6f7179`. Accent red `#f73b20` (gradient `135deg, #f8a4a4 → #f73b20`).
Radius scale built on `var(--radius)` (× .5/2/4) + `999px`. Easings `--ease-out cubic-bezier(0,0,.2,1)` ·
`--ease-in-out cubic-bezier(.4,0,.2,1)`. `@keyframes shimmer · pulse · enter · exit`. Display 44/28/25px.

**Page structure.** "High-quality DESIGN.md examples for AI agents" → "Give your AI agent real design taste"
→ filter pills (Minimal · Clean SaaS · Editorial Type · Soft Gradients · Monochrome · Playful · High Contrast ·
Premium) → **Trending / Popular / Newest** tabs → gallery with **poetic one-line descriptions** (Apple
"Gallery wall at natural light", Mercury "Mountain Top Command Center", Home "Broadsheet financial broadside",
Ui "brutalist Swiss grid in graphite", Resend "Obsidian developer terminal"). Get Refero **MCP**.

**Adopt → Tadfuq.** **Poetic one-line descriptors** for each service/section (gives soul to a directory);
filter-pill taxonomy + tabbed gallery for the services directory (§6.13).

---

## 6 · aura.build — AI design generator

**Exact tokens.** Fonts `Inter` + `Google Sans Flex` + `Geist` + **`Newsreader` (serif!)** + `Geist Mono`.
Accent blue `#2563eb`. Radii `8px`, `var(--radius)`, `9999px`, `1.5rem`. Display scale **3.75 / 3 / 2.25 /
1.875rem** (60/48/36/30px). Easings `.4,0,.2,1` · `.16,1,.3,1` · `.25,1,.5,1`. **Conic border-spin**
`conic-gradient(from calc(var(--gradient-angle)+45deg),black,transparent 10% 90%,black)`. Shadow
`0 3px 6px #00000026` + `inset 0 .5px #777`. `@keyframes fadeSlideIn · columnReveal · border-spin · breathe ·
sonar · beam-spin · marquee-scroll · float`.

**Page structure.** Hero = **AI prompt composer** (Design-System chip + model dropdown + attach) over faint
**column-grid guides**; eyebrow pill announces the model; **tri-state theme toggle**; "Trending" generated-site gallery.

**Adopt → Tadfuq.** Faint **column-grid background guides**; **tri-state theme toggle** (light/auto/dark);
the conic **border-spin** as a rare "processing" affordance (gated, gold/indigo, reduced-motion off).

---

## 7 · neuform.ai — prompt-to-production (the richest dark/glass system)

**Exact tokens.** Fonts **`DM Sans`** (display) + `IBM Plex Mono` + `JetBrains Mono`. Pure `#000` + `#050505`
+ white, with **white-alpha surfaces** `rgba(255,255,255,.05/.06/.08/.10/.12)` (depth by alpha, not gray).
Accent **Discord-blurple** `#5865f2 / #4d5ae2 / #626fff / #5461ec`. **Radius `999px` (198×!)** + `8/10/12/6` +
`var(--radius-md)`. **Glass card** `linear-gradient(145deg,#121720db,#0a0c12e0) padding-box, var(--glass-border-gradient)`
with **`backdrop blur(18px) saturate(130%)`** (and `blur(8px) saturate(120%)`). Shadow
`0 14px 30px #00000047, inset 0 1px #ffffff08` (lift + top inner highlight). **Mono labels at 9–12px / .58–.76rem.**
Easings `cubic-bezier(.16,1,.3,1)` (20×) · `.22,1,.36,1` · `.24,.84,.24,1`. Button gradient `linear-gradient(180deg,#5865f2,#4d5ae2)`.
`@keyframes auth-shell-fade-up · -square-in · -stripe-in · loader-border-glimmer · loader-text-glimmer`.

**Page structure / bento.** Dark auth panel (mono eyebrow, "Continue with Google" pill + circular arrow,
**avatar social-proof "24.4K"**). Showcase cards: a blue-gradient starburst; a **dark "Global Telemetry"
particle-sphere dashboard** (mono `NODE_A88 SYNCING`, **LIVE FEED** rows, KPI `12,042 NODES · 24.8 TB/s`);
a **horizontal accordion** (`01/DIRECTION` orbit illustration · `02/EXPERIENCE` · `03/IDENTITY`, collapsed to
vertical labels — "Select a card to explore"); an editorial "Bold Ideas" + B&W photo.

**Adopt → Tadfuq.** This is our **dark-mode bible**: depth by **white-alpha steps** + top inner highlight
(matches our Indigo Dusk glow elevation); glass `blur(18px) saturate(130%)`; **mono labels 9–12px**; the
**horizontal domain accordion** (§6.11) and **telemetry/KPI dashboard** (§6.12) were lifted from here. We
swap blurple → our indigo `#8E94FF` on dark.

---

## 8 · typeui.sh — "build better UI with AI"

**Exact tokens.** Fonts **`Geist` + `Geist Mono`**. Ink `#18181b / #000`, canvas `#fafafa`, warm `#f5f0e8`.
Accents amber `#f59e0b`, blue `#007acc` + `#2563eb`, teal `#34e8bb`. Radii `9999px` + `var(--radius-2xl/3xl/sm)`.
**Double focus ring** `0 0 0 2px #fff, 0 0 0 6px #00000014` (and inverse on dark). Easings `cubic-bezier(.16,1,.3,1)`,
the silky **`cubic-bezier(.32,.72,0,1)`**, `(0,0,.2,1)`. **Page-rail gutter gradients**
`linear-gradient(to right,#000 0,#000 var(--page-rail-gutter-width),transparent …)`. `@keyframes
homepage-tool-rotate-in/out · marquee · integration-card-glow · -waves · -bar-pulse`.

**Page structure (full marketing page).** H1 "Build better UI with AI using Codex/Claude/Cursor" →
**Create a brand kit · Build an MVP · Build where you want · Give your AI a real design system · Spend fewer
tokens · Make your UI convert · Ship polished UI faster** → FAQ (14) → "Supported by" → **Choose a design
skill** (Paper · Neumorphism · Bento · Perspective). Pricing **Monthly / Yearly (Save 67%)**. Inline stat
strip "77 design skills · 449 prompts · 7,168 users".

**Adopt → Tadfuq.** **Double-ring focus** option for high-emphasis controls; the silky `.32,.72,0,1` easing
for drawer/sheet slides; **inline stat strip**; **page-rail gutter** framing for wide layouts.

---

## 9 · open-design.ai — open-source agent design platform

**Exact tokens.** Fonts `Albert Sans` (sans) + serif + mono + `Remix Icon`. Palette: `--paper #fafafa` ·
`--paper-warm #f5f5f5` · `--ink #262626` · `--ink-soft #434343` · `--ink-mute #595959` · `--ink-faint #8c8c8c`
· **green accents** `#63fe13 / #83ff3b / #218c00` + lime tints `#d8ffb5 / #beff8c / #f2ffe6` (note: `color-mix(in
oklab, var(--bone), var(--coral) 8%)` tints). Radii `50% · 999px · 8 · 6 · 16 · 9 · 12px`. Easings **expo-out
`cubic-bezier(.23,1,.32,1)`** (36×) · `.22,.61,.36,1`. **Real liquid glass:** `backdrop: url(#nav-liquid-glass)
blur(7px) saturate(1.4)` + `blur(26px) saturate(108%)`. Layered glass shadow `inset 0 0 2px 1px #ffffff8c, inset
0 0 10px 4px #ffffff38, 0 6px 24px #11111a0f`. `@keyframes contributor-orbit-spin(-rev) · blurTextIn · marquee-x`.

**Page structure.** H1 "Open Design — Open-source Claude Design alternative" → "From idea to delivery" →
"What can you make" (Prototype/Dashboard/Slides/Image/Video/Design System) → "Plug in 21+ coding agents" →
**stats 52K+ Stars · 280+ Contributors · 217+ Plugins · 129+ Design Systems · 21 Agents** → contributors orbit → FAQ.

**Creative devices.** Blueprint grid + golden-ratio spiral guides + scattered 3D tool props; **green Figma
selection-box framing the headline**; SVG-filter liquid glass on the nav; **blurTextIn** reveal.

**Adopt → Tadfuq.** **expo-out `cubic-bezier(.23,1,.32,1)`** as an alt entrance for big reveals; the
SVG-filter liquid glass approach (chrome only); blueprint+golden-ratio hero guides; a **blur-in text** reveal
for the masthead (reduced-motion safe). Their green is theirs — we stay indigo/gold.

---

## 10 · liquid-glass-oss (playground) — WebGL glass

**Exact tokens.** SF Pro. Accent **iOS blue `#0a84ff`** (`--lg-accent`) + `#6657ed` purple + `#58a6ff`.
Dark `#0a0a0c / #050506 / #252529 / #29292e`. Radii `999px` (22×) · `50%` · `12/14/16/24/8`. Glass shadows
`inset 0 1px #ffffffe6, 0 1px 4px #0000002e` + lift `0 24px 70px #00000047`. **Backdrop `blur(18–20px)
saturate(130–135%)`**. Easing `cubic-bezier(.2,.8,.2,1)`. **Liquid `@keyframes`**: `lg-liquid-window-in/out ·
lg-liquid-droplet-in · lg-liquid-bridge-in` with vars `--lg-droplet-from-y:-72px · --lg-bridge-from-y:-34px`
(a droplet "morph + bridge" entrance). Surface gradients `linear-gradient(180deg,#fff,#f8f8fb)`; green toggle
`#63d565→#53c957`.

**Physics panel defaults (from the studio UI):** Blur `.18` · Refraction `.12` · Chromatic `.045` ·
Distortion `.015` · Edge light `.08` · Specular `.14` · Fresnel `1.08` · Radius `22` · Depth `42`.

**Adopt → Tadfuq.** Our glass-chrome defaults (`blur 18–20px saturate 130%`, edge highlight `inset 0 1px
rgba(255,255,255,.9)`); the physics numbers as a starting point **for chrome only, readability-gated**; the
"droplet morph" is too playful for an ops tool — *reject* for work surfaces.

---

## 11 · getdesign.md — the DESIGN.md catalog (source of our 8 refs)

**Exact tokens.** Mono + sans on `#000`. Grayscale ramp `#a0a0a0 · #404040 · #808080 · #c0c0c0 · #dfdfdf ·
#ededed`. Accents pink `#ffb1ee` + yellow `#ff0` + orange `#e3971c`. **Icon-tile radius `25%`** (52×).
Shadow `0 1px 2px rgba(0,0,0,0.6), inset 0 1px 0 rgba(255,255,255,0.05)` (dark inset). Pink **shimmer sweep**
`linear-gradient(110deg, transparent 30%, rgba(255,177,238,.35) 50%, transparent 70%)`; grid-line bg gradient.
Display leading `1.05`. `@keyframes catalog-shimmer · catalog-pulse · fade-up · heartbeat · marquee`.

**Page structure.** H1 "Production-grade DESIGN.md analysis" → **Quick Stats** (75 files, "Follows Google's
official DESIGN.md spec") → **Find Designs**: category sidebar with counts (AI & LLM 12 · Dev Tools 7 ·
Backend/DB/DevOps 8 · SaaS 9 · Design 6 · Fintech 7 · E-commerce 5 · Media 14 · Automotive 7) + search +
**table** (favicon · name · one-line description · `New` · Installs · Bookmarked). Maintained by VoltAgent.

**Adopt → Tadfuq.** The **category-sidebar + searchable directory table + KPI columns** (§6.13 services
directory); the **shimmer-sweep** for loading rows; "follows the Google spec" — which our `design.md` does.

---

## 12 · bestdesignsonx.com — the curated X gallery

**Exact tokens.** Fonts `Inter` + `Plus Jakarta Sans` + `Geist` + **`Instrument Serif`** (← the serif-italic
emphasis word). **OKLCH grayscale** (shadcn): `oklch(98.5% 0 0)` / `oklch(20.5% 0 0)` / `oklch(14.5% 0 0)` /
`oklch(55.6% 0 0)`. Accents purple `#cc8ef5` + blue `#074de5`. Radii `.25rem · 4px · 50% · 100px · var(--radius-2xl)`.
Shadow `0 4px 12px #0000001a, 0 0 0 2px #0003`. `@keyframes enter · exit · swipe-out-left/right/up/down`
(card-swipe) + `sonner` toasts.

**Page structure.** Serif header "Best *Designs* on X.com" (one word blue italic), "Updated hourly", a
**list / grid / masonry** switch over an **8,000+ item bento gallery** mixing light-neumorphic widgets,
dark-premium cards, pastel mesh gradients, 3D-spot icons, and brand-kit bentos.

**Adopt → Tadfuq.** The **masonry/bento services gallery** + view-mode switch; **Instrument Serif** is a good
candidate for our serif-italic emphasis word; OKLCH neutral ramp confirms our OKLCH section-hue approach;
*reject* the card-swipe (dating-app gesture, wrong register for ops).

---

## 13 · designmd.me & designmd.supply — DESIGN.md generators

SPA shells (tokens JS-bundled). **Observed:** designmd.me = **dark navy + dotted grid + purple glow**
(≈ our Indigo Dusk), display with **blue serif-italic** emphasis, **URL-input hero** + "Try:" pills
(apple/stripe/linear/github/notion), a "WHAT YOU GET" two-card checklist (`NEW` badge, purple-glow border).
Inline accents = Vercel blue `#0070f3 / #3291ff`, system fonts. designmd.supply = **warm off-white**
(≈ our Walnut Ivory), left-aligned editorial display with **gray serif-italic**, pill domain input + dark
round arrow, gallery of **brand cards = thumbnail + favicon + `domain · category` + 3-dot swatch trio**.

**Adopt → Tadfuq.** designmd.me validates **Indigo Dusk + serif-italic** almost 1:1; adopt the **try-pills**
and **two-card checklist**; designmd.supply's **brand card w/ swatch trio** → §6.14.

---

## 14 · GitHub repos (context, not visual sources)

- **google-labs-code/design.md** — the spec we conform to: **v0.3.0, 16.3k★, Apache-2.0**, `@google/design.md`
  CLI, PHILOSOPHY.md, docs for all CSS color formats. → confirms lint-in-CI is supported.
- **mattpocock/skills** — "Skills for Real Engineers" **142k★, MIT, v1.0.1** (`.claude-plugin`, `skills/`,
  CLAUDE.md). → reference for maintaining our `.kiro/skills/`.
- **docker/awesome-compose** — Compose samples; **not a design source** (kept for transparency).

---

## Cross-site synthesis — the patterns that repeat (and our verdict)

| Pattern | Seen on | Tadfuq verdict |
|---------|---------|----------------|
| **Single chromatic accent + glow CTA** | kinetics, backgrounds, apple-ref, authkit-ref | **Adopt** — indigo action; gold glow for the ceremonial moment only |
| **Serif-italic emphasis word** in a sans display | bestdesignsonx, backgrounds, designmd.me/.supply, refero | **Adopt** — one phrase per heading (Instrument Serif / Boska) |
| **Mono "stamped" labels + live readouts/KPIs** | kinetics, neuform, getdesign, typeui | **Adopt** — eyebrows, KPI strip, telemetry, IDs (`tnum`+`zero`) |
| **Depth by surface/alpha steps + 1px inset highlight, not drop shadow** | neuform, liquidglass, seed-ref, apple-ref | **Adopt** — our §4 elevation (light shadow / dark glow) |
| **Glass on chrome only:** `blur 18–22px saturate 130%` + edge highlight | neuform, liquidglass, open-design, dia-ref | **Adopt** — top bar / modal / receipt, readability-gated |
| **Position-shift tonal gradient** on the primary button | gradientbuttons | **Adopt** — indigo CTA only |
| **Bento / masonry gallery + view switch** | bestdesignsonx, neuform | **Adopt** — services gallery (§7) |
| **Category sidebar + searchable table + KPI columns** | getdesign.md | **Adopt** — services directory (§6.13) |
| **Horizontal accordion for categories** | neuform | **Adopt** — domain accordion (§6.11) |
| **Draughtsman framing** (crosshair / selection-box / blueprint + golden-ratio) | coverflow, open-design, authkit-ref | **Adopt sparingly** — one hero moment |
| **Edge-fade marquee mask** | backgrounds, aura, typeui | **Adopt** — tickers/scrollers |
| **Expo-out / silky easings** `(.23,1,.32,1)`, `(.32,.72,0,1)` | open-design, typeui | **Adopt** — big reveals / sheet slides |
| **Tri-state theme toggle; GitHub-star + avatar social proof** | aura, typeui, coverflow, neuform | **Adopt toggle**; social-proof N/A for internal tool |
| **Poetic one-line descriptors** per item | refero | **Adopt** — gives the services directory soul |
| **Neo-brutalist all-mono; card-swipe; droplet morph; featherweight wt300** | hyperbrowser; bestdesignsonx; liquidglass; dia/seed-ref | **Reject** — wrong register for a civic ops tool |

> **Bottom line.** The ecosystem converges on: **one warm/lifted canvas, one rationed accent, tight display
> tracking, mono structural labels, depth-by-light-not-shadow, glass-on-chrome-only, and one signature per
> screen** — exactly the spine of `design.md`. The genuinely new, directly-useful imports for an *operations*
> product are the **services directory table**, the **horizontal domain accordion**, the **dark telemetry/KPI
> dashboard**, and the **serif-italic emphasis word** — all now folded into the system.
