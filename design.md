---
# ───────────────────────────────────────────────────────────────────────────
# design.md — Tadfuq Al-Khayr Design System (machine-readable token layer)
# Spec: google-labs/design.md (YAML front matter + markdown rationale).
# Validate: npx @google/design.md lint design.md
# ───────────────────────────────────────────────────────────────────────────
version: alpha
name: Tadfuq Al-Khayr
description: >
  Civic atelier at golden hour. A subscriber-services operations platform that
  reads like a premium civic broadsheet rendered in software — indigo gravitas,
  gilded ceremonial moments, walnut-ivory calm by day and lifted indigo dusk by
  night. Arabic-first, RTL by default, dual-theme, anti-slop. One signature per
  screen.

colors:
  # Canonical keys (so the agent never auto-generates the palette)
  primary:       "#2B3180"   # Royal Indigo — the only first-class action color
  secondary:     "#9B1C2E"   # Heritage Crimson — urgent / destructive / section lead
  tertiary:      "#B0851F"   # Warm Gilt — ceremonial only
  neutral:       "#F6F2E9"   # Walnut Ivory — canvas
  # Light — Walnut Ivory canvas
  bg:            "#F6F2E9"
  bg-2:          "#EFEADC"
  surface:       "#FFFFFF"
  surface-2:     "#FBF8F1"
  surface-3:     "#F2ECDD"
  border:        "#E4DDCB"
  border-2:      "#D4C9AF"
  ink:           "#1A1714"
  ink-2:         "#4A453C"
  ink-3:         "#897F6B"
  # Identity — royal indigo + heritage crimson + warm gilt
  indigo:        "#2B3180"
  indigo-soft:   "#3A41A6"
  crimson:       "#9B1C2E"
  crimson-soft:  "#C24151"
  gold:          "#B0851F"
  gold-soft:     "#D8B255"
  # Semantic
  ok:            "#2F7D55"
  warn:          "#B0791A"
  err:           "#A83232"
  info:          "{colors.indigo}"
  # Section identity (1:1 with the four service domains; OKLCH, extendable)
  section-cs:    "oklch(0.52 0.13 262)"   # Subscriptions — Cobalt
  section-ct:    "oklch(0.58 0.10 70)"    # Technical — Bronze
  section-cb:    "oklch(0.56 0.09 195)"   # Billing — Teal
  section-ca:    "oklch(0.53 0.11 15)"    # Complaints & Reports — Rosewood

typography:
  display:
    fontFamily: Clash Display, Alexandria, Readex Pro, Georgia, serif
    fontSize: 4.5rem
    fontWeight: 600
    lineHeight: "1.05"
    letterSpacing: "-0.025em"
  h1:
    fontFamily: Clash Display, Alexandria, Readex Pro, serif
    fontSize: 3rem
    fontWeight: 600
    lineHeight: "1.12"
    letterSpacing: "-0.02em"
  h2:
    fontFamily: Clash Display, Alexandria, Readex Pro, serif
    fontSize: 2rem
    fontWeight: 500
    lineHeight: "1.18"
    letterSpacing: "-0.015em"
  body-lg:
    fontFamily: General Sans, Readex Pro, IBM Plex Sans Arabic, system-ui, sans-serif
    fontSize: 1.125rem
    fontWeight: 400
    lineHeight: "1.6"
  body:
    fontFamily: General Sans, Readex Pro, IBM Plex Sans Arabic, system-ui, sans-serif
    fontSize: 1rem
    fontWeight: 400
    lineHeight: "1.6"
  caption:
    fontFamily: General Sans, Readex Pro, system-ui, sans-serif
    fontSize: 0.8125rem
    fontWeight: 400
    lineHeight: "1.45"
  eyebrow:
    fontFamily: JetBrains Mono, Geist Mono, ui-monospace, monospace
    fontSize: 0.75rem
    fontWeight: 500
    lineHeight: "1.2"
    letterSpacing: "0.12em"
  mono:
    fontFamily: JetBrains Mono, Geist Mono, ui-monospace, monospace
    fontSize: 0.875rem
    fontWeight: 400
    lineHeight: "1.5"
    fontFeature: "tnum"

rounded:
  sm:   8px
  md:   12px
  lg:   16px
  xl:   20px
  "2xl": 28px
  pill: 999px

spacing:
  "1":  4px
  "2":  8px
  "3":  12px
  "4":  16px
  "5":  20px
  "6":  24px
  "8":  32px
  "10": 40px
  "12": 48px
  "16": 64px
  "20": 80px
  "24": 96px
  "30": 120px

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.surface}"
    rounded: "{rounded.pill}"
  button-ceremonial:
    backgroundColor: "{colors.tertiary}"
    textColor: "{colors.ink}"
    rounded: "{rounded.pill}"
  button-danger:
    backgroundColor: "{colors.secondary}"
    textColor: "{colors.surface}"
    rounded: "{rounded.pill}"
  service-card:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
    rounded: "{rounded.2xl}"
    padding: "{spacing.6}"
  top-bar:
    backgroundColor: "{colors.surface}"
    textColor: "{colors.ink}"
---

# Tadfuq Al-Khayr — Design System
> civic atelier at golden hour — indigo gravitas, gilded moments, walnut-ivory calm.

**Theme:** dual (light + dark) · **Direction:** RTL-first (Arabic), LTR-safe · **Density:** comfortable

> **What this file is.** The single source of design truth for the Tadfuq Al-Khayr
> subscriber-services platform. It supersedes `DESIGN0001.md` — that file documented a
> competent but muted "quiet institutional" system; this one keeps its discipline (tokens,
> anti-slop rigor, the four-domain color logic) and elevates it into something with a real
> point of view: confident, warm, and quietly luxurious. The YAML front matter above is the
> normative token layer (lint with `npx @google/design.md lint design.md`); the prose below
> is the rationale and the craft rules. **Read this before touching any UI.**

---

## 0 · Overview — the north star

Tadfuq Al-Khayr is a **subscriber-services operations platform**: people come here to act on a
subscriber's account — open and track requests, route cases across branches, issue forms and
fees, file and resolve complaints, run reports. The job is serious and repetitive, so the design
must do two things at once: **disappear when work is dense**, and **feel premium when it matters**.

The voice is a **civic atelier at golden hour**. Picture a high-end public institution — a
national archive, a central bank lobby, a contemporary museum of records — lit warm. By day the
canvas is **Walnut Ivory**: an off-white with a toasted, nutty undertone (`#F6F2E9`) that reads
as paper, not screen. By night it becomes **Indigo Dusk**: a lifted navy-indigo (`#161B36`),
never OLED-black — calm, cool, and easy on long shifts. A single **royal indigo** carries every
primary action; **heritage crimson** marks the urgent and the destructive and leads section
mastheads; **warm gilt gold** is rationed for ceremonial moments only (a completed receipt, a VIP
flag). Color does structural work, never decoration.

Three principles govern everything:

1. **One signature per screen.** Borrowed from Apple's "black void, one lit object" and
   Authkit's "single saturated accent." Each view earns exactly one moment that draws the eye —
   a kinetic masthead, a gilt seal, a Cover-Flow showcase. If two elements compete, delete the
   weaker one.
2. **Elevation by light, not by drop shadow.** Following Authkit/Seed/Dia: depth comes from
   hairline inset strokes, soft indigo-tinted ambient shadow (light) or a faint glow (dark) —
   never heavy gray boxes.
3. **Restraint is the luxury.** Tight negative tracking on display type, generous section gaps,
   muted neutrals, and a tiny vocabulary of chromatic accents. The expensive look comes from
   what we leave out.

**Audience:** Arabic-speaking service staff and administrators. **Platform:** web, `<html dir="rtl">`
by default, responsive 375 → 1440+. **Class prefixes (runtime):** `f-` / `ff-` / `fui-` / `adm-`
remain valid; new work builds **additively** on the `--f-*` token layer (see §12 migration).

---

## 1 · Colors

The palette is **two warm-tinted neutral ramps** (one per theme) plus **three identity accents**
and **four section hues**. Neutrals do 90% of the work; accents are precious.

### 1.1 Light — Walnut Ivory

| Name | Value | Token | Role |
|------|-------|-------|------|
| Walnut Ivory | `#F6F2E9` | `bg` | Page canvas — warm toasted off-white, the "paper" of the system. Never pure white. |
| Ivory Shade | `#EFEADC` | `bg-2` | Recessed zones, sticky-header backdrop, alternating bands. |
| Snow | `#FFFFFF` | `surface` | Primary card / panel surface — one clean step above canvas. |
| Linen | `#FBF8F1` | `surface-2` | Inputs, nested surfaces, table headers. |
| Parchment | `#F2ECDD` | `surface-3` | Pressed / selected / hover fill on warm surfaces. |
| Hairline | `#E4DDCB` | `border` | Default 1px borders and dividers. |
| Hairline Strong | `#D4C9AF` | `border-2` | Emphasis dividers, input focus borders. |
| Ink | `#1A1714` | `ink` | Primary text — warm near-black, not `#000`. |
| Ink Muted | `#4A453C` | `ink-2` | Secondary text, body copy under headings. |
| Ink Faint | `#897F6B` | `ink-3` | Captions, metadata, placeholders. **Never for body — fails AA.** |

### 1.2 Dark — Indigo Dusk

| Name | Value | Token | Role |
|------|-------|-------|------|
| Indigo Dusk | `#161B36` | `bg` | Page canvas — lifted deep indigo-navy, calm not black. |
| Dusk Shade | `#1B2142` | `bg-2` | Recessed zones and bands. |
| Slate Panel | `#222A4F` | `surface` | Primary card / panel surface. |
| Slate Raised | `#2A3358` | `surface-2` | Inputs, nested surfaces, table headers. |
| Indigo Line | `#353F6B` | `border` | Borders and dividers. |
| Moon Ink | `#EAE7DE` | `ink` | Primary text — warm off-white (echoes the ivory day). |
| Moon Muted | `#B7B9C9` | `ink-2` | Secondary text. |
| Moon Faint | `#8488A0` | `ink-3` | Captions, metadata. Not for body. |

### 1.3 Identity accents (both themes)

| Name | Light | Soft | Dark-mode | Token | Role |
|------|-------|------|-----------|-------|------|
| Royal Indigo | `#2B3180` | `#3A41A6` | `#8E94FF` | `indigo` | **The only first-class action color.** Primary buttons, active states, focus ring, links. |
| Heritage Crimson | `#9B1C2E` | `#C24151` | `#E07385` | `crimson` | Urgent + destructive actions; the **leading rule** on section mastheads. Never a generic accent. |
| Warm Gilt | `#B0851F` | `#D8B255` | `#E3C268` | `gold` | **Ceremonial only** — completed receipt, VIP flag, milestone. One gold moment per flow, maximum. |

### 1.4 Semantic

`ok #2F7D55` · `warn #B0791A` · `err #A83232` (err ≈ crimson family — keep distinct from the
crimson *brand* mark by context) · `info` = `{colors.indigo}`.

### 1.5 Section hues — the four domains (OKLCH, extendable)

Each service domain owns **one** hue, used 1:1 — for its masthead rule, card edge, icon tile, and
active tab. **Do not reuse a section hue decoratively elsewhere.** Bind it per-surface with a local
custom property `--section-c` (replaces the runtime `--d-c`).

| Code | Domain | Light | Dark (L lifted ~0.72) | Hue name |
|------|--------|-------|------------------------|----------|
| **CS** | Subscriptions | `oklch(0.52 0.13 262)` | `oklch(0.72 0.12 262)` | Cobalt |
| **CT** | Technical | `oklch(0.58 0.10 70)` | `oklch(0.74 0.09 70)` | Bronze |
| **CB** | Billing | `oklch(0.56 0.09 195)` | `oklch(0.73 0.08 195)` | Teal |
| **CA** | Complaints & Reports | `oklch(0.53 0.11 15)` | `oklch(0.72 0.10 15)` | Rosewood |

> **Extending:** a 5th domain (e.g. **CX** — Field/Outage) takes the next perceptually-even hue,
> e.g. `oklch(0.55 0.10 145)` (Sage). Keep chroma ≤ 0.13 and L 0.50–0.58 (light) so all sections
> sit at one perceived "weight." Add it to the front matter as `section-cx` and document here.

> **Color psychology (why these):** Indigo = trust, authority, competence — the institution's
> backbone. Crimson = urgency and consequence — reserved so it never cries wolf. Gold = reward and
> ceremony — scarcity makes it feel earned. Warm ivory lowers cognitive load on a screen people
> stare at for hours; lifted indigo at night reduces glare without the harshness of pure black.

---

## 2 · Typography

Three families, each with an Arabic counterpart so RTL never falls back to a system serif.
**Banned everywhere:** Inter, Roboto, Arial (carryover guardrail — they read as "default/unconsidered").

| Family | Token | Latin / Arabic | Role |
|--------|-------|----------------|------|
| **Clash Display** / **Alexandria** | `display` | display + headings | Mastheads, hero, section titles, big numbers. Distinctive, confident, slightly editorial. |
| **General Sans** / **Readex Pro** | `body` | UI + body | Everything functional: labels, body, tables, forms. Calm humanist sans. |
| **JetBrains Mono** / *(latin only)* | `mono` | codes + labels | Request IDs, case numbers, status codes, KPI numerals (tabular), and **eyebrow labels**. |

> Fonts via [fontshare.com](https://www.fontshare.com) (Clash Display, General Sans) and Google
> Fonts (Alexandria, Readex Pro, JetBrains Mono). Substitute chain in front matter keeps RTL safe.

### 2.1 Type scale

| Role | Size (clamp / fixed) | Weight | Line height | Tracking | Token |
|------|----------------------|--------|-------------|----------|-------|
| display | `clamp(2.2rem→4.5rem)` | 600 | 1.05 | −0.025em | `display` |
| h1 | `clamp(1.9rem→3rem)` | 600 | 1.12 | −0.02em | `h1` |
| h2 | `clamp(1.4rem→2rem)` | 500 | 1.18 | −0.015em | `h2` |
| h3 | 1.25rem | 500 | 1.25 | −0.01em | — |
| body-lg | 1.125rem | 400 | 1.6 | — | `body-lg` |
| body | 1rem | 400 | 1.6 | — | `body` |
| caption | 0.8125rem | 400 | 1.45 | — | `caption` |
| eyebrow | 0.75rem | 500 | 1.2 | **+0.12em** caps | `eyebrow` |
| mono | 0.875rem | 400 | 1.5 | `tnum` | `mono` |

**The eyebrow is a signature.** Mono, uppercase, wide-tracked, ink-faint — it precedes mastheads
and labels structural zones ("SUBSCRIPTIONS · CS", "RECEIPT", "STEP 2 OF 3"). It telegraphs
"this is structure, not content," exactly like Authkit's `dotDigital` and Seed's mono codes.
For Arabic, the eyebrow uses Readex Pro at 0.75rem with `+0.04em` (Arabic doesn't take caps/wide
Latin tracking) — keep the *role*, adapt the *mechanics*.

**Numerals are tabular** (`font-feature-settings: "tnum"`) in tables, KPIs, money, and IDs so
columns align and digits don't jitter on update.

---

## 3 · Layout & spacing

- **Base unit:** 4px. Scale: `4 · 8 · 12 · 16 · 20 · 24 · 32 · 40 · 48 · 64 · 80 · 96 · 120`.
- **App shell max-width:** 1480px (dense operational views). **Marketing/landing bands:** 1200px.
- **Section gap:** 96–120px on marketing, 48–64px between operational blocks.
- **Card padding:** 24px standard, 32px on hero/featured cards.
- **Grid:** 12-col fluid; service grids use `repeat(auto-fill, minmax(280px, 1fr))`.
- **Touch targets:** ≥ 44px. **Focus ring:** 2px `indigo` at 38% + 2px offset (cobalt-bright in dark).
- **Logical properties only** — `margin-inline`, `padding-block`, `inset-inline-start`, `border-start-*`.
  Never `left`/`right`. This is what makes RTL "just work."

---

## 4 · Elevation & depth

Depth is built from **four layers of light**, never a single gray drop shadow.

**Light theme**
- *Hairline:* `inset 0 0 0 1px {colors.border}` — the base definition on every surface.
- *Lift (cards):* `0 1px 2px rgba(26,23,20,.04), 0 8px 24px -12px rgba(43,49,128,.14)` — indigo-tinted, soft, directional-down.
- *Hover lift:* raise the second value to `0 14px 32px -14px rgba(43,49,128,.20)` + `translateY(-2px)`.
- *Pressed:* drop to hairline only.

**Dark theme**
- *Hairline:* `inset 0 0 0 1px {colors.border}`.
- *Glow lift:* `0 0 0 1px rgba(142,148,255,.10), 0 12px 40px -16px rgba(0,0,0,.6)` + a faint top inner highlight `inset 0 1px 0 rgba(234,231,222,.06)`.
- Surfaces lift by **color step** (`bg → surface → surface-2`), not by bigger shadows.

**Never:** warm/black box-shadows, `0 2px 4px rgba(0,0,0,.25)`-style default shadows, or stacking
shadows to fake importance. Importance comes from the one signature, not from shadow weight.

---

## 5 · Shapes & motion

**Radius:** `sm 8 · md 12 · lg 16 · xl 20 · 2xl 28 · pill 999`. Cards `2xl`/`xl`; inputs/buttons
`md`; pills/avatars/tags `pill`. Soft, tactile, object-like (Apple's machined feel) — but not
bubbly. Keep one radius family per component cluster.

**Motion tokens**

```
--ease-standard : cubic-bezier(.4, 0, .2, 1)
--ease-entrance : cubic-bezier(.16, 1, .3, 1)     /* decelerate in */
--ease-exit     : cubic-bezier(.4, 0, 1, 1)       /* accelerate out */
--spring-soft   : linear(...) | cubic-bezier(.34,1.3,.64,1)  /* damped, ≤6% overshoot */
--dur-micro : 180ms   --dur-enter : 280ms   --dur-exit : 200ms
```

- **Animate only** `transform`, `opacity`, `filter`, `color`, `box-shadow`. **Never** layout
  properties (width/height/top/margin) — they thrash and jank.
- **Exit faster than entrance** (200 vs 280). Things leave decisively, arrive gently.
- **Spring with weight, not with bounce.** From [kinetics.colorion.co](https://kinetics.colorion.co):
  use spring *feel* for delight moments (the gilt seal settling, a counter tick, a magnetic CTA),
  but **clamp overshoot ≤ 6%** — this is a work tool, not a toy. Big elastic bounce is banned.
- **`prefers-reduced-motion: reduce`** disables all entrance choreography, springs, and the kinetic
  masthead; transitions collapse to a 1-frame opacity swap. Non-negotiable.

---

## 6 · Components

### 6.1 Buttons
- **Primary** — `indigo` fill, `surface` text, `pill` radius, 12×24 padding. A subtle **tonal brand
  gradient** (`indigo → indigo-soft`, ~12° ) is allowed *only here* (idea from
  [gradientbuttons.colorion.co](https://gradientbuttons.colorion.co)); hover shifts the gradient
  *position*, not its hue, and lifts 1px. Max one primary per viewport.
- **Secondary / ghost** — transparent, 1px `border-2`, `ink` text. Carries presence via the hairline.
- **Ceremonial** — `gold` fill, `ink` text. Reserved for receipt download / VIP confirm. Rare.
- **Danger** — `crimson` fill, used in destructive confirms only.
- **Magnetic affordance (optional):** the single hero CTA may pull ~25–35% toward the cursor inside
  its hover zone (kinetics "magnet"), resetting on leave — desktop + pointer:fine only, off under
  reduced-motion.

### 6.2 Service card — the centerpiece
The object subscribers' services are presented through. Three illustration tiers (see §7), one anatomy:

```
┌─────────────────────────────────────────────┐
│  ⬡ illustration (top-inline-end)             │   ← 3D spot / line+mesh / iso
│                                               │
│  SUBSCRIPTIONS · CS        (eyebrow, mono)    │
│  New Connection Request    (h3, ink)          │
│  Open and route a new meter…  (caption, ink-2)│
│                                               │
│  4 open  ·  ~2d avg        (mono, tnum)       │   ← live stats, optional
│  ───────────────────────── (section edge)     │
└─────────────────────────────────────────────┘
   border-start: 3px {--section-c}   radius 2xl   surface
```

- Left/inline-start edge carries `--section-c` (3px). Hover = §4 hover-lift + a **cursor-following
  radial glow** in `--section-c` at ~6% (owned by one layer — never double-apply).
- Featured/hero card uses the **3D spot** illustration and `surface` + inner top highlight.
- Standard grid cards use **line+mesh** illustrations and stay flat until hover.

### 6.3 Top bar (chrome) — liquid glass
Sticky, translucent: `backdrop-filter: blur(20px) saturate(140%)` over `surface` at **≥ 72% opacity**
(must stay readable in light — no `white/10`), 1px bottom hairline, a top sheen edge. The
[liquidglass-oss](https://gitlab.com/ogtirth/liquidglass-oss) `feDisplacementMap` refraction is for
**chrome only** (top bar, modal scrim, receipt) — never on text. Firefox fallback via `@supports`
→ plain blur. Holds: brand lockup (inline-start), domain tabs (center), theme toggle + user (inline-end).

### 6.4 Tabs / segmented nav
Pill container, active segment fills `surface` with hairline + `--section-c` underline; inactive
`ink-2`. Animate the active indicator with `transform` (shared-layout slide), `--ease-standard`.

### 6.5 Forms & tables
**Flat and quiet — no effects here.** Inputs: `surface-2` fill, 1px `border`, `md` radius, focus =
indigo ring. Tables: `tnum` numerals, `surface-2` header, hairline row dividers, hover row tint
`surface-3`. Density comfortable; never animate table content.

### 6.6 Stepper (request flows)
Vertical connected stepper (echoing the finance reference's transfer flow): numbered nodes joined by
a 2px rail, active node filled `--section-c`, completed nodes a small check, upcoming nodes hairline.
One active step at a time; the eyebrow reads "STEP n OF m".

### 6.7 Receipt — the gilt moment
The ceremonial peak. Glass card, a single **gilt seal** (SVG, `gold`) that settles in with a damped
spring, mono reference number (`tnum`), and a ceremonial download button. **This is the one place
gold + spring + glass converge** — and it happens once per completed flow.

### 6.8 Services showcase — Cover Flow (optional, onboarding/landing)
For featured services or first-run onboarding, an iOS-style Cover Flow
([coverflow.ashishgogula.in](https://coverflow.ashishgogula.in)): spring-physics, **zero layout shift**
(isolated transforms only), keyboard arrow-key navigation, velocity-aware drag. Not for dense
operational lists — those stay as grids/tables.

### 6.9 Empty / loading / error states
Empty = a calm **isometric** illustration + one-line guidance + single primary action. Loading =
content-shaped skeletons (`surface-2` → `surface-3` shimmer via `transform`, not width). Error =
crimson hairline + plain message + retry. Never spinners-as-decoration.

### 6.10 KPI strip
Row of mono `tnum` values with caption labels and tiny trend marks; numbers may **tick** on update
with a ≤6% spring bump (kinetics "number counter"), reduced-motion → instant.

---

## 7 · Imagery & illustration system

A **deliberate mix of three tiers** (your call) — each with a clear job, never blended randomly:

1. **3D spot — soft & glossy (hero / featured only).** A single rounded, lightly neumorphic object
   per card (a coil, a meter, a document seal), lit warm, sitting in `--section-c`. Premium, tactile,
   used sparingly so it stays special. *Source palette/feel:* curated handcrafted gradients à la
   [backgrounds.supply](https://www.backgrounds.supply) — rebuilt on our tokens, never lifted.
2. **Line + mesh (standard grid cards).** A 1.5px monoline glyph over a very faint radial mesh wash
   in `--section-c` (≤ 8%). This is the workhorse — calm, scalable, Notion/Stripe-clean.
3. **Isometric (overviews / empty states / section landings).** Light-depth isometric scenes that
   explain a domain at a glance, in the section hue + neutrals only.

**Rules:** icons are SVG monoline at 1.5px stroke (Material Symbols or custom) — **never emoji**.
Each illustration uses the **section hue + neutrals**, no rainbow. One illustration tier per surface
context. Grain (≤5% light / ≤7% dark) + a sub-8% mesh may texture the canvas (backgrounds.supply
principle) — never behind data tables or long text.

---

## 8 · Do's and Don'ts

### Do
- Keep **one signature per screen**; if two elements compete, cut the weaker.
- Use `indigo` as the **only** primary-action color; everything else is ghost/neutral.
- Reserve `gold` for a single ceremonial moment per flow; reserve `crimson` for urgent/destructive + section leads.
- Build elevation from **hairline insets + soft indigo-tinted shadow / dark glow**.
- Lead every masthead with an eyebrow (mono, `+0.12em`, caps) and a crimson rule.
- Bind section identity through `--section-c`, 1:1 with the four domains.
- Use `tnum` numerals for all data, money, and IDs.
- Animate `transform`/`opacity`/`filter` only; exit faster than entrance; honor reduced-motion.
- Keep glass readable in light (`surface ≥ 72%`); restrict refraction to chrome.

### Don't
- **No "AI" purple/indigo *decorative* gradients**, no gradient-on-text (`background-clip:text`) — impeccable flags it; use solid `ink`.
- No bounce/elastic easing; springs stay damped (≤6% overshoot).
- No heavy gray/black drop shadows; no stacking shadows to fake importance.
- No emoji as icons; no Inter / Roboto / Arial; no raw hex/px/ms outside the token layer.
- No physical `left`/`right` — logical properties only.
- No effects on tables/forms; no rainbow illustrations; no second primary CTA in a viewport.
- Don't reuse a section hue decoratively outside its domain.

---

## 9 · Surfaces — when-to-use matrix

| Surface | Allowed | Forbidden here |
|---------|---------|----------------|
| Page masthead (h1) | kinetic line-level entrance (once), crimson lead rule, eyebrow | glass, gradient fill |
| Primary CTA | tonal brand gradient + position-shift hover, magnetic pull | glass distortion |
| Top bar / modal / receipt | liquid glass (blur+saturate+sheen), receipt = gilt seal + spring | kinetic type |
| Canvas (`body`) | grain ≤5/7%, sub-8% mesh in section hue | animated rainbow, color behind tables |
| Service cards | `--section-c` edge + cursor-glow, 3D/line/iso by tier | loud full gradient |
| Tables / forms | nothing — flat, quiet, readable | every effect above |
| KPI / counters | ≤6% spring tick on update | continuous looping motion |

---

## 10 · Inspiration bank (the analyzed source library)

> **Method.** Every site below was studied for its *principle*, not its pixels. We **rebuild on our
> own `--f-*` tokens**, never copy code or assets, never exceed ~30 consecutive words from any source,
> and cite on use. *Content rephrased for compliance with licensing restrictions.* This is the
> creative fuel — return here when a screen feels flat.

| # | Source | Type | What we extract | Verdict on our identity |
|---|--------|------|------------------|--------------------------|
| 1 | [bestdesignsonx.com](https://bestdesignsonx.com) | Curated gallery of standout design shared on X (ever-updating) | Composition, hierarchy, taste, current craft trends — a **discovery feed** | **Reference** — extract the principle, never pixel-copy |
| 2 | [kinetics.colorion.co](https://kinetics.colorion.co) | 72 spring-physics interactions (CSS + React + AI prompt, live stiffness/damping) | "Motion with weight": damped springs for the gilt seal, KPI tick, magnetic CTA | **Adapt** — clamp overshoot ≤6%; delight moments only |
| 3 | [ripplix.com](https://ripplix.com) | UI animation / micro-interaction library | Micro-interaction vocabulary (focus, toggles, toasts, hover reveals) | **Adapt** — micro only, within motion budget |
| 4 | [coverflow.ashishgogula.in](https://coverflow.ashishgogula.in) | iOS Cover Flow for React (spring, zero layout shift, a11y) | Services showcase / onboarding carousel pattern | **Use** — featured/onboarding, not dense lists |
| 5 | [gradientbuttons.colorion.co](https://gradientbuttons.colorion.co) | CSS gradient button gallery | Tonal brand gradient + position-shift hover | **Adapt** — primary CTA only, brand hues |
| 6 | [liquidglass-oss](https://gitlab.com/ogtirth/liquidglass-oss) | Apple liquid glass (CSS/SVG `feDisplacementMap`) | Backdrop blur + saturate + sheen edge + refraction | **Adapt** — chrome only; Firefox fallback |
| 7 | [backgrounds.supply](https://www.backgrounds.supply) | 1,167 curated gradient/grain/mesh backgrounds | Production-ready grain + mesh depth, color moods | **Use** — subtle canvas texture, rebuilt on tokens |
| 8 | [styles.refero.design](https://styles.refero.design) | 2,000+ AI-readable DESIGN.md examples | Refined design language to borrow/benchmark | **Reference** — pairs with `refero-design` skill |
| 9 | [google-labs design.md](https://github.com/google-labs-code/design.md) | The DESIGN.md spec + `npx @google/design.md lint` | Front-matter token schema, section order, WCAG lint | **Use** — this file conforms; lint in CI |
| 10 | [open-design.ai](https://open-design.ai) | Open-source agent-native design platform + portable DESIGN.md | Brand-extraction → DESIGN.md flow, skill protocol | **Reference** — pairs with `open-design` skill |
| 11 | [typeui.sh](https://typeui.sh) | Copy-paste AI UI section prompts (anti-slop, conversion) | Section layout starting points (hero, pricing, nav) | **Reference** — prompts, then re-skin to our tokens |
| 12 | [aura.build](https://aura.build) · [neuform.ai](https://neuform.ai) | AI UI/site generators (neuform = neumorphic) | Generative starting points; neumorphic softness for 3D spot tier | **Reference** — direction only, hand-finish to tokens |
| 13 | [github.com/mattpocock/skills](https://github.com/mattpocock/skills) | Agent skills library | Skill authoring patterns | **Reference** — for skill maintenance |
| 14 | [docker/awesome-compose](https://github.com/docker/awesome-compose) | Docker Compose samples | — *not a design source* | **Excluded** — listed for honesty/transparency |

---

## 11 · Skills (installed — activate before working in-domain)

Mirrored in `.kiro/skills/` (and `.claude/skills/`, `.agents/skills/`). Same eleven as the prior system.

| # | Skill | When to use |
|---|-------|-------------|
| 1 | **refero-design** | Research-first UI methodology + craft rules (type, color, spacing, motion, a11y, anti-slop). Activate for any UI work. RTL/Arabic-first. |
| 2 | **design-md** | Extract/author this file from a design system. Activate when updating `design.md` or extracting tokens from a site. |
| 3 | **open-design** | Artifact-first generation + 5-axis critique + anti-AI-slop checklist + DESIGN.md outline. Activate when generating/critiquing UI pre-ship. |
| 4 | **awesome-design-md** | 70+ ready DESIGN.md files from real products. Activate to borrow refined language fast or seed a page. |
| 5 | **frontend-design** | Intentional, distinctive visual direction; avoid template defaults. |
| 6 | **impeccable** | 44-pattern slop detector. `npx impeccable detect <path>` must return `[]`. Run after every CSS change. |
| 7 | **design-taste-frontend** | Anti-slop for landing/portfolio/redesign — audit-first, non-templated. |
| 8 | **animate** | React/Next animation patterns (Emil Kowalski "Animations on the Web"). Activate for transitions/hover/modals. |
| 9 | **design-motion-principles** | Motion expert (Kowalski + Krehel + Tompkins). Build with purposeful motion, or audit existing motion. |
| 10 | **ui-ux-pro-max** | Searchable base: 67 styles · 96 palettes · 57 pairings · 99 UX rules. `python steering/ui-ux-pro-max/scripts/search.py "<q>" --design-system`. |
| 11 | **creative-fx** | Our library built from the inspiration sources (kinetic/glass/gradient/grain + gallery), adapted to `--f-*`. See `.kiro/skills/creative-fx/references/`. |

---

## 12 · Migration from DESIGN0001 (`--f-*` continuity)

This system is an **evolution, not a rewrite**. The runtime keeps `--f-*` tokens and `f-/ff-/fui-/adm-`
classes. Apply this layer **additively** in a last-loaded stylesheet — do not edit the core.

| Old (`--f-*`) | New role | Action |
|---------------|----------|--------|
| `--f-bg #fafaf7` | Walnut Ivory | retune → `#F6F2E9` (warmer, nuttier) |
| `--f-navy #1e2a4d` | Royal Indigo | deepen/enrich → `#2B3180` (primary action) |
| `--f-crimson #8f1d28` | Heritage Crimson | keep role → `#9B1C2E` |
| `--f-gold #b8861b` | Warm Gilt | keep, ceremonial-only → `#B0851F` |
| `--d-c` (per-card) | `--section-c` | rename; same 1:1 domain logic |
| dark `--f-bg #131720` | Indigo Dusk | lift/indigo-shift → `#161B36` |

**Carry over unchanged:** the cache lesson (version CSS links `?b=N`, hard-reload to verify), the
specificity discipline (`.f3d .X` beats `.X`), the collision check before any `::after`/`box-shadow`
(e.g. the `final_micro` card glow is owned — don't double it), and the verification loop:
`npx impeccable detect` → `[]`, then Playwright at 375/768/1440, toggle dark, confirm reduced-motion.

---

## 13 · Agent prompt guide

### Quick color reference
- text primary: `#1A1714` (light) / `#EAE7DE` (dark)
- text body: `#4A453C` / `#B7B9C9`
- text muted: `#897F6B` / `#8488A0`
- background: `#F6F2E9` / `#161B36`
- surface: `#FFFFFF` / `#222A4F`
- border: `#E4DDCB` / `#353F6B`
- primary action: `#2B3180` (Royal Indigo) — the only CTA color
- ceremonial: `#B0851F` (Warm Gilt) · urgent/destructive: `#9B1C2E` (Heritage Crimson)

### Example component prompts

**Service card (CS / Subscriptions):** White surface, 28px radius, 24px padding, 3px inline-start
edge in `oklch(0.52 0.13 262)`. Top-inline-end: a soft 3D-spot coil illustration in the cobalt hue.
Eyebrow "SUBSCRIPTIONS · CS" in JetBrains Mono 12px, `+0.12em`, `#897F6B`. Title "New Connection
Request" in Clash Display 20px/500, `#1A1714`. One-line caption in General Sans 16px, `#4A453C`. A
mono `tnum` stat row "4 open · ~2d avg". Hover: lift `translateY(-2px)` + indigo-tinted soft shadow
+ a 6% cobalt cursor-following glow. No drop shadow, no full gradient.

**Primary CTA:** Royal Indigo `#2B3180` pill (radius 999px), white text in General Sans 16px/500,
12×24 padding, subtle tonal gradient `#2B3180 → #3A41A6` at 12°. Hover shifts gradient position +1px
lift; optional magnetic pull ~30% toward cursor (pointer:fine, off under reduced-motion).

**Top bar (liquid glass):** Sticky, `backdrop-filter: blur(20px) saturate(140%)` over `#FFFFFF` at
74% opacity, 1px bottom hairline `#E4DDCB`, top sheen edge. Brand lockup inline-start, domain tabs
center (active = `--section-c` underline), theme toggle + avatar inline-end. Firefox: plain blur.

**Receipt (gilt moment):** Glass card, centered SVG gilt seal in `#B0851F` that settles via a damped
spring (≤6% overshoot), mono `tnum` reference number, ceremonial gold download button. One gold
moment per flow.

**Empty state:** Calm isometric illustration in the section hue + neutrals, one-line guidance in
General Sans 18px `#4A453C`, single Royal Indigo primary action. No spinner.

---

## 14 · Similar brands (north-star neighbors)

- **Notion** — warm-neutral calm, restrained color, content-first density; our Walnut Ivory + quiet tables.
- **Vercel** — single saturated accent on a disciplined neutral canvas; CSS-rendered product surfaces.
- **Apple** — "one lit object," tight display tracking, machined soft radii, silence as a tool.
- **Origin Financial / Superhuman** — editorial gravitas + a rationed chromatic moment; our gilt seal & indigo.
- **Seed** — single-hue discipline, pill forms, flat-but-warm; our section-hue 1:1 logic.

---

## 15 · Verification & workflow

1. Activate the relevant skill (§11); read `creative-fx` references if using an effect.
2. Build **additively** on `--f-*` in a last-loaded layer; never edit the core needlessly.
3. **Collision check** before any `::after`/`box-shadow`/glow — is the element already owned?
4. **Specificity check** — match the existing selector depth so your rule actually wins.
5. Verify: `npx impeccable detect <path>` → `[]`; then `npx @google/design.md lint design.md`;
   then Playwright at 375 / 768 / 1440; toggle dark; confirm `prefers-reduced-motion`; check AA contrast.
6. **One signature per screen.** If two compete, delete the weaker.

---

## 16 · Known gaps (carryover + new)

- **Charts:** section hues exist, but a full data-viz palette (series order, sequential/diverging
  ramps on Walnut Ivory & Indigo Dusk) is not yet specified. Next deliverable.
- **Breakpoints** are not yet centralized as tokens (per-component media queries today).
- **3D-spot illustration assets** need a production pipeline (source/style lock) so the tier stays
  consistent rather than ad-hoc.
- **"World-class" taste** still needs a visual review loop: change small → screenshot → repeat;
  value-checking alone can't judge aesthetics.

---

## 17 · Quick start (copy-paste tokens)

Tech-neutral by design: the CSS custom-property block is the source; the Tailwind v4 and React
snippets are conveniences on top of it. **The runtime keeps its `--f-*` names** — these `--ds-*`
names are the canonical export; alias them to `--f-*` in the last-loaded layer during migration (§12).

### 17.1 CSS custom properties (light + dark)

```css
:root {
  /* ── Light · Walnut Ivory ─────────────────────────── */
  --ds-bg: #F6F2E9;        --ds-bg-2: #EFEADC;
  --ds-surface: #FFFFFF;   --ds-surface-2: #FBF8F1;  --ds-surface-3: #F2ECDD;
  --ds-border: #E4DDCB;    --ds-border-2: #D4C9AF;
  --ds-ink: #1A1714;       --ds-ink-2: #4A453C;      --ds-ink-3: #897F6B;

  /* ── Identity ─────────────────────────────────────── */
  --ds-indigo: #2B3180;    --ds-indigo-soft: #3A41A6;   /* primary action */
  --ds-crimson: #9B1C2E;   --ds-crimson-soft: #C24151;  /* urgent / lead   */
  --ds-gold: #B0851F;      --ds-gold-soft: #D8B255;     /* ceremonial only */
  --ds-ok: #2F7D55; --ds-warn: #B0791A; --ds-err: #A83232; --ds-info: var(--ds-indigo);

  /* ── Section hues (bind per-surface to --section-c) ── */
  --ds-cs: oklch(0.52 0.13 262);  /* Subscriptions · Cobalt   */
  --ds-ct: oklch(0.58 0.10 70);   /* Technical · Bronze        */
  --ds-cb: oklch(0.56 0.09 195);  /* Billing · Teal            */
  --ds-ca: oklch(0.53 0.11 15);   /* Complaints · Rosewood     */

  /* ── Type ─────────────────────────────────────────── */
  --ds-font-display: "Clash Display", "Alexandria", "Readex Pro", Georgia, serif;
  --ds-font-body:    "General Sans", "Readex Pro", "IBM Plex Sans Arabic", system-ui, sans-serif;
  --ds-font-mono:    "JetBrains Mono", "Geist Mono", ui-monospace, monospace;
  --ds-fs-display: clamp(2.2rem, 1.4rem + 3.6vw, 4.5rem);
  --ds-fs-h1:      clamp(1.9rem, 1.4rem + 2vw, 3rem);
  --ds-fs-h2:      clamp(1.4rem, 1.1rem + 1.2vw, 2rem);
  --ds-fs-body: 1rem; --ds-fs-caption: 0.8125rem; --ds-fs-eyebrow: 0.75rem;
  --ds-track-display: -0.025em; --ds-track-eyebrow: 0.12em;

  /* ── Space · radius ───────────────────────────────── */
  --ds-1:4px; --ds-2:8px; --ds-3:12px; --ds-4:16px; --ds-5:20px; --ds-6:24px;
  --ds-8:32px; --ds-10:40px; --ds-12:48px; --ds-16:64px; --ds-20:80px; --ds-24:96px; --ds-30:120px;
  --ds-r-sm:8px; --ds-r-md:12px; --ds-r-lg:16px; --ds-r-xl:20px; --ds-r-2xl:28px; --ds-r-pill:999px;

  /* ── Motion ───────────────────────────────────────── */
  --ds-ease-standard: cubic-bezier(.4,0,.2,1);
  --ds-ease-entrance: cubic-bezier(.16,1,.3,1);
  --ds-ease-exit: cubic-bezier(.4,0,1,1);
  --ds-spring-soft: cubic-bezier(.34,1.3,.64,1);   /* damped, ≤6% overshoot */
  --ds-dur-micro:180ms; --ds-dur-enter:280ms; --ds-dur-exit:200ms;

  /* ── Elevation (light) ────────────────────────────── */
  --ds-hairline: inset 0 0 0 1px var(--ds-border);
  --ds-lift: 0 1px 2px rgba(26,23,20,.04), 0 8px 24px -12px rgba(43,49,128,.14);
  --ds-lift-hover: 0 1px 2px rgba(26,23,20,.04), 0 14px 32px -14px rgba(43,49,128,.20);
  --ds-ring: 0 0 0 2px color-mix(in srgb, var(--ds-indigo) 38%, transparent);
}

/* ── Dark · Indigo Dusk (lifted, never OLED) ────────── */
:root[data-theme="dark"], :root.dark {
  --ds-bg: #161B36;        --ds-bg-2: #1B2142;
  --ds-surface: #222A4F;   --ds-surface-2: #2A3358;  --ds-surface-3: #313B63;
  --ds-border: #353F6B;    --ds-border-2: #45517F;
  --ds-ink: #EAE7DE;       --ds-ink-2: #B7B9C9;      --ds-ink-3: #8488A0;
  --ds-indigo: #8E94FF;    --ds-crimson: #E07385;    --ds-gold: #E3C268;
  --ds-cs: oklch(0.72 0.12 262); --ds-ct: oklch(0.74 0.09 70);
  --ds-cb: oklch(0.73 0.08 195); --ds-ca: oklch(0.72 0.10 15);
  --ds-hairline: inset 0 0 0 1px var(--ds-border);
  --ds-lift: 0 0 0 1px rgba(142,148,255,.10), 0 12px 40px -16px rgba(0,0,0,.6), inset 0 1px 0 rgba(234,231,222,.06);
  --ds-lift-hover: 0 0 0 1px rgba(142,148,255,.16), 0 18px 48px -16px rgba(0,0,0,.66), inset 0 1px 0 rgba(234,231,222,.08);
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation: none !important; transition-duration: 1ms !important; }
}
```

### 17.2 Tailwind v4 (`@theme`)

```css
@theme {
  --color-bg: #F6F2E9;        --color-bg-2: #EFEADC;
  --color-surface: #FFFFFF;   --color-surface-2: #FBF8F1;  --color-surface-3: #F2ECDD;
  --color-border: #E4DDCB;    --color-border-2: #D4C9AF;
  --color-ink: #1A1714;       --color-ink-2: #4A453C;      --color-ink-3: #897F6B;
  --color-indigo: #2B3180;    --color-indigo-soft: #3A41A6;
  --color-crimson: #9B1C2E;   --color-gold: #B0851F;
  --color-ok: #2F7D55; --color-warn: #B0791A; --color-err: #A83232;
  --color-cs: oklch(0.52 0.13 262); --color-ct: oklch(0.58 0.10 70);
  --color-cb: oklch(0.56 0.09 195); --color-ca: oklch(0.53 0.11 15);

  --font-display: "Clash Display", "Alexandria", "Readex Pro", Georgia, serif;
  --font-sans:    "General Sans", "Readex Pro", "IBM Plex Sans Arabic", system-ui, sans-serif;
  --font-mono:    "JetBrains Mono", "Geist Mono", ui-monospace, monospace;

  --radius-sm:8px; --radius-md:12px; --radius-lg:16px; --radius-xl:20px; --radius-2xl:28px;
  --ease-entrance: cubic-bezier(.16,1,.3,1);
  --ease-exit: cubic-bezier(.4,0,1,1);
}
/* Dark variant driven by [data-theme="dark"] — see CSS block above for overrides. */
```

### 17.3 React — service card (RTL-safe, section-hued)

```tsx
// Uses logical properties + a per-card --section-c. Tailwind classes map to the @theme tokens.
type Domain = "cs" | "ct" | "cb" | "ca";

function ServiceCard({ domain, eyebrow, title, summary, stat }: {
  domain: Domain; eyebrow: string; title: string; summary: string; stat?: string;
}) {
  return (
    <article
      dir="rtl"
      style={{ ["--section-c" as string]: `var(--ds-${domain})` }}
      className="group relative rounded-[28px] bg-surface p-6
                 [border-inline-start:3px_solid_var(--section-c)]
                 shadow-[var(--ds-lift)] transition-[transform,box-shadow]
                 duration-[var(--ds-dur-enter)] ease-[var(--ds-ease-entrance)]
                 hover:-translate-y-0.5 hover:shadow-[var(--ds-lift-hover)]
                 motion-reduce:transition-none motion-reduce:hover:translate-y-0"
    >
      <p className="font-mono text-[0.75rem] tracking-[0.12em] uppercase text-ink-3">{eyebrow}</p>
      <h3 className="mt-1 font-display text-xl font-medium tracking-[-0.01em] text-ink">{title}</h3>
      <p className="mt-2 text-ink-2 leading-relaxed">{summary}</p>
      {stat && (
        <p className="mt-4 font-mono text-sm text-ink-2 [font-feature-settings:'tnum']">{stat}</p>
      )}
    </article>
  );
}
```

### 17.4 Motion — damped spring (delight only, kinetics-derived)

```css
/* The gilt seal / KPI tick / confirm check. Settles with weight, ≤6% overshoot — never bouncy. */
@keyframes ds-settle {
  0%   { transform: scale(.82); opacity: 0; }
  60%  { transform: scale(1.05); opacity: 1; }   /* tiny, single overshoot */
  100% { transform: scale(1); }
}
.ds-seal { animation: ds-settle var(--ds-dur-enter) var(--ds-spring-soft) both; }
@media (prefers-reduced-motion: reduce) { .ds-seal { animation: none; } }
```

---

> **In one line:** build on `--f-*`, activate the right skill, borrow the *principle* not the code,
> check collisions and specificity, pass impeccable + design.md lint + Playwright + reduced-motion,
> and protect the one signature per screen. Walnut-ivory calm, indigo gravitas, a single gilded moment.
