# Handoff: Personal Portfolio — "Crimson Edition"

## Overview
A premium, cinematic single-page personal portfolio for **Aung Khant Hein** — a multidisciplinary maker (Web Developer · Video/Photo Editor · Prompt Engineer · Translator). The site is designed to bridge technical logic (code / AI) with creative craft (editing / design) through a film-still visual language built around a signature crimson accent that echoes the subject portrait's lighting.

The visitor should leave with a clear sense of the four services, a portfolio proof of range, and one obvious CTA: send an email.

---

## About the Design Files

The files bundled here (`Portfolio.html` and `assets/portrait.jpg`) are **design references authored in HTML/CSS/JS**. They are a prototype demonstrating the intended look, layout, motion, and interaction — **not production code to ship verbatim**.

The task is to **recreate this design inside the target codebase's existing environment** (React, Vue, Astro, SvelteKit, Next.js, etc.) using its established component patterns, styling system (Tailwind / CSS-in-JS / SCSS modules), routing conventions, and asset pipeline.

If no codebase exists yet, the recommended starting stack is:
- **Next.js 14+ (App Router)** or **Astro** for a marketing/portfolio site of this scope
- **Tailwind CSS** for design tokens (all values below map cleanly to Tailwind config)
- **Framer Motion** or **GSAP** for the animations (typewriter, scroll reveal, marquee)
- **next/font** (or equivalent) for the Google Fonts (Fraunces, Space Grotesk, JetBrains Mono)

## Fidelity

**High-fidelity (hifi).** The prototype includes final colors, typography, spacing, copy, and interactions. Recreate pixel-perfectly. Hex values, font weights, and easing curves in this document are authoritative.

---

## Screens / Views

This is a **single-page scroll site** with 8 stacked sections. There are no separate routes. The nav uses `#anchor` links with `scroll-behavior: smooth`.

### Global chrome (persistent across the page)

- **Custom cursor**: a 10×10 px crimson dot that lags the mouse with easing (0.22 lerp). Grows to 42×42 px paper-colored on hover over interactive elements. Uses `mix-blend-mode: difference`. Hidden on touch devices via `@media (hover: none)`.
- **Film grain overlay**: fixed, full-viewport, `z-index: 9999`, `opacity: 0.06`, `mix-blend-mode: overlay`. Inline SVG feTurbulence noise. Do not skip — it's a load-bearing texture element.
- **Fixed nav bar**: 22px top/40px side padding, backdrop-blur(14px) + saturate(140%) over `rgba(10,10,11,0.55)`, 1px bottom border `rgba(255,255,255,0.05)`.

### Nav

- **Logo (left)**: 9×9px crimson dot with 12px crimson glow shadow, followed by "Aung Khant Hein" in Fraunces 500 22px.
- **Nav links (center-right)**: `01 About · 02 Arsenal · 03 Work · 04 Process · 05 Contact`. Number prefix is JetBrains Mono 10px, crimson, superscript, 6px right margin. Link text is Space Grotesk 13.5px, opacity 0.78 → 1 on hover.
- **CTA button (far right)**: Pill button, 1px `rgba(255,255,255,0.15)` border, radius 999px, JetBrains Mono 12px. Contains a 6×6px green (`#4ade80`) status dot with a 1.6s pulse animation (opacity 1→0.35→1), then "Available for work". Hover: border + background flip to crimson.
- Hides `.nav-links` on `max-width: 820px`.

### 1. Hero

- **Layout**: 2-column grid, `1.15fr 0.85fr`, 60px gap, min-height 100vh, top padding 140px (below nav), bottom 80px.
- **Background glow**: absolute-positioned radial gradient, `rgba(230,57,70,0.35) → transparent`, 800×800px, 60px blur, positioned at `right: -10%, top: 20%`.

**Left column (copy):**
1. **Eyebrow** — "Portfolio · Vol. 04 · MMXXVI", JetBrains Mono 12px, crimson, letter-spacing 0.15em, uppercase. Preceded by a 40×1px crimson line, 14px gap.
2. **H1 headline** — Fraunces 300, `clamp(48px, 7.4vw, 118px)`, line-height 0.92, letter-spacing -0.035em. Three lines:
   `Building the`
   `bridge between`
   `<em>logic & art.</em>` — italic + crimson + weight 400
3. **Role rotator** — "Currently operating as **[typewriter slot]**". Slot is a 140px-min-width inline block, Space Grotesk, with a 2×14px crimson caret animated at 1s steps(2) blink. Roles cycle every ~2.2s with typewriter-in (40ms/char) and erase (22ms/char):
   - a Video Editor
   - a Prompt Engineer
   - a Translator
   - a Web Developer
   - a Multidisciplinary Maker
4. **Description** — 17px, `--bone` color, max-width 500px. Text: *"I'm **Aung Khant Hein** — a multidisciplinary maker who codes like an engineer, edits like a filmmaker, prompts like a poet, and translates with the precision of a diplomat. Four disciplines. One relentless standard."* Bold text uses `--paper`, weight 500.
5. **CTA row** — Two buttons, 16px gap:
   - **Primary** ("View selected work"): crimson bg, paper text, 18/32 padding, radius 999px, 14px/500 weight, arrow icon 18×18px. Shadow `0 12px 40px -8px rgba(230,57,70,0.55)`. Hover: bg → `--ember` (#FF5A67), translateY(-2px), stronger shadow. Arrow translates (3px, -3px) on hover.
   - **Ghost** ("Start a project"): transparent, 1px `rgba(255,255,255,0.15)` border, 18/26 padding, envelope icon. Hover: border → paper, bg → `rgba(255,255,255,0.04)`.

**Right column (portrait stack):**
- Container is `aspect-ratio: 4/5`, max-height 640px, position relative.
- **Portrait frame**: absolute inset:0, radius 6px, overflow hidden, `--char` background, shadow `0 40px 80px -20px rgba(0,0,0,0.8), 0 0 0 1px rgba(255,255,255,0.06)`. Image is `object-fit: cover`, `filter: contrast(1.05) saturate(1.05)`.
- **Bracket corners**: two 24×24px paper-colored L-corners via `::before` (top-left, `border-right:0; border-bottom:0`) and `::after` (bottom-right, `border-left:0; border-top:0`), 10px inset. Reads as film-still crop marks.
- **Corner text (film-camera HUD)**: JetBrains Mono 10px, `--bone`, letter-spacing 0.15em, absolute, 14px inset:
  - Top-left: `◉ REC`
  - Top-right: `04:20:26`
  - Bottom-left: `SUBJ // 01`
- **Portrait badge**: absolute `bottom: -18px; right: -18px`. Paper background, obsidian text, 16/22 padding, radius 4px, `0 20px 40px -10px rgba(0,0,0,0.6)` shadow. Contains crimson mono 10px "NOW STREAMING" label, then body "Available for select freelance engagements, Q3 – Q4 2026." (11px, 1.5 line-height, uppercased, 0.15em tracking).

**Hero meta strip** (`bottom: 40px; left: 40px; absolute`):
- 4 items, 40px gap, mono 11px, `--ash`, uppercase, 0.12em tracking.
- Each: uppercase label + `<strong>` value below (paper, 500 weight, 0.05em tracking).
- Items: `Based: Remote · Southeast Asia`, `Response time: < 12 hours`, `Languages: EN · ID · JP · ES`, `Clients since: 2021`.

**Responsive**: at `max-width: 900px`, grid collapses to single column, portrait max-height 500px / max-width 380px, meta strip becomes static below.

### 2. Marquee band (between hero and About)

- 30px vertical padding, `--char` background, 1px `rgba(255,255,255,0.08)` top + bottom borders, overflow hidden.
- Track: flex, 60px gap, animated `translateX(0 → -50%)` over 40s linear infinite.
- Content: Fraunces 300 44px, letter-spacing -0.02em, alternating between plain words ("Development", "Prompt Engineering") and italic crimson ("*Editing*", "*Translation*") separated by gold (`#E9B949`) `✦` diamonds.
- Duplicate the sequence so the loop is seamless.

### 3. Section header pattern (reused for all `.block` sections)

Every content section uses this header structure:
- 140px top+bottom padding (90px on mobile).
- 2-column grid: `200px 1fr`, 60px gap, `align-items: end`, 80px bottom margin.
- **Left column** — section number: `01 / Origin` in JetBrains Mono 12px crimson uppercase (0.2em tracking), then a subtitle line in `--ash` below with 6px top margin.
- **Right column** — section title: Fraunces 300, `clamp(36px, 5vw, 72px)`, line-height 1.02, letter-spacing -0.03em, max-width 900px. Italic-crimson `<em>` for accent phrases.
- On `max-width: 720px`, collapses to single column with 24px gap and 50px bottom margin.

### 4. About Me — `01 / Origin`

- Section number: `01 / Origin` — "The person behind the pixels"
- Title: "I don't pick a lane. I engineer where the *lanes converge.*"
- 2-column grid below (`1.2fr 1fr`, 80px gap, `align-items: start`).
- **Left** — Lede paragraph: Fraunces 300, 32px, line-height 1.25, letter-spacing -0.015em. Italic-crimson for `<em>rational</em>`, `<em>romantic</em>`, and `<em>where the seam is</em>` phrases.
- **Right** — Body: 3 paragraphs, 16px Space Grotesk, `--bone` color, line-height 1.75, 22px paragraph spacing, max-width 480px.
- **Stat row** (below right column): 60px top margin, 40px top padding, 1px `rgba(255,255,255,0.08)` top border. 3-col grid, 30px gap. Each stat: Fraunces 300 56px number with crimson `<em>` on the numeral, then JetBrains Mono 11px `--ash` uppercase label (12px above). Stats: **120+** Projects shipped · **4** Core disciplines · **28** Countries served.

### 5. The Arsenal (Services) — `02 / Arsenal`

- Section has `--char` (`#131316`) background (differs from body).
- Header: "Four disciplines. *One studio.* Zero compromises on craft."
- **Grid**: 2 columns, 1px gap on `rgba(255,255,255,0.08)` background, 1px outer border, radius 8px, overflow hidden — creates hairline dividers between cards.
- **Service card**: `--char` bg, 50/44 padding, min-height 380px, flex column.
  - Top-line reveal: `::before` element, 2px crimson bar, animates width 0 → 100% on hover over 0.5s `cubic-bezier(.7,0,.3,1)`.
  - Hover background flip: `--char` → `--graphite` over 0.4s.
  - **Head row**: mono service number (`/ 01`) crimson left, 44×44px circular icon right (1px border, hover: crimson bg). Icon SVGs 20×20px, 1.6 stroke.
  - **h3**: Fraunces 400 32px, letter-spacing -0.02em, italic-crimson `<em>`. 12px below.
  - **Body**: 15px, `--bone`, 1.65 line-height, flex-grow to push tags down.
  - **Tags row**: flex-wrap 8px gap. Each tag: JetBrains Mono 10.5px, 6/12 padding, 1px `rgba(255,255,255,0.12)` border, radius 999px, `--bone` color, uppercase 0.05em tracking.

**Four cards (exact copy):**

1. **/ 01 — Web *Development*** — icon: brackets + slash
   > Responsive, blazing-fast, production-grade websites and web apps. I write clean, maintainable code that ships on time and loads before your visitor blinks. Performance isn't a feature here — it's the foundation.
   Tags: `React · Next.js` `TypeScript` `Tailwind` `Node · Postgres` `CMS integration`

2. **/ 02 — Video & Photo *Editing*** — icon: film strip
   > Cinematic edits, colour-graded to feel. Whether it's a launch film, a wedding highlight, or a 15-second scroll-stopper — I edit for rhythm, weight, and mood. Every cut earns its place; every frame is intentional.
   Tags: `DaVinci Resolve` `Premiere Pro` `After Effects` `Lightroom · Photoshop` `Colour grading`

3. **/ 03 — Prompt *Engineering*** — icon: sun/star burst
   > The AI whisperer. I architect prompts that make LLMs produce work indistinguishable from a domain expert — for copy, code, ideation, or automation. If your AI stack feels generic, you don't have a model problem. You have a prompting problem.
   Tags: `GPT · Claude · Gemini` `Prompt architecture` `Agent workflows` `Fine-tuning briefs` `Eval harnesses`

4. **/ 04 — *Translation* & Localization** — icon: language "A/文" motif
   > Translation is 20% linguistics and 80% culture. I don't move words between languages — I move meaning, tone, and intent. Marketing copy that lands. UI strings that don't break. Subtitles that keep the joke funny in every dialect.
   Tags: `EN ↔ ID` `EN ↔ JP` `EN ↔ ES` `Subtitle timing` `Transcreation`

Mobile: grid collapses to single column, 40/28 padding, min-height:auto.

### 6. Selected Work — `03 / Selected Work`

- Header: "Case studies from across *the disciplines.*"
- **Asymmetric 6-column grid**, 24px gap. Six project cards with variable spans:
  - Card 1 — `wide` (span 4, `aspect-ratio: 4/3`) — Meridian SaaS
  - Card 2 — `tall` (span 2, `aspect-ratio: 3/4`) — North of Nowhere doc trailer
  - Card 3 — `med` (span 3) — Copybot prompt library
  - Card 4 — `sm` (span 2) — JP indie game localization
  - Card 5 — `med` (span 3) — Ruma Kopi brand film
  - Card 6 — `med` (span 3) — Nord & Co. site launch
- **Card structure**:
  - Radius 6px, `--graphite` background, overflow hidden, `cursor: none`.
  - Hover: `translateY(-6px)` over 0.5s `cubic-bezier(.2,.9,.3,1)`.
  - **Visual layer** (absolute inset:0) — 4 background treatments:
    - `type-a`: `radial-gradient(ellipse at 30% 30%, #3a1114 0%, #0d0507 70%)`
    - `type-b`: `linear-gradient(135deg, #1a1a1e 0%, #0a0a0b 100%)`
    - `type-c`: `linear-gradient(200deg, #2d0e10 0%, #0f0708 60%)`
    - `type-d`: `radial-gradient(circle at 70% 40%, #1a1a1c 0%, #0a0a0b 80%)`
  - **Decorative motifs** inside visuals (choose per card):
    - `viz-orb`: 55% wide circle, radial crimson gradient, `float` animation (translateY -12px, scale 1.02, 8s ease-in-out infinite).
    - `viz-lines`: 32×32px grid of `rgba(255,255,255,0.04)` lines.
    - `viz-glyph`: Fraunces italic 300, 180px, `--paper` at 0.15 opacity — used for translation card (`言`) and Ruma card (`R` at crimson 0.4 opacity, 140px).
    - `viz-triangle`: 90/90/156px crimson triangle with 40px crimson drop-shadow.
    - `viz-code`: JetBrains Mono 11px, `rgba(230,57,70,0.35)` (or gold variant), 40px padding, whitespace pre. Used for Copybot card (prompt text) and Nord & Co. card (build output). Full snippets in `Portfolio.html`.
  - **Info overlay** (absolute bottom, 26px padding, gradient `rgba(0,0,0,0.85) → transparent`):
    - Kicker: JetBrains Mono 10.5px crimson uppercase 0.15em (e.g. `Web · Full-stack · 2026`).
    - Title: Fraunces 400 22px, letter-spacing -0.01em.
    - Right side: 40×40px circular arrow badge, 1px `rgba(255,255,255,0.2)` border. Hover: fill crimson, rotate -45deg.

- Mobile: all cards collapse to single column, `aspect-ratio: 4/3`.

### 7. Philosophy quote block — `04 / Philosophy`

- Section has `--char` background, 160px vertical padding, overflow hidden.
- Giant background quote glyph: `"` in Fraunces italic 500px, crimson at 0.08 opacity, positioned `top:-80px; left:-40px`.
- Section header (only left column used): `04 / Philosophy — The through-line`.
- **Quote**: Fraunces 300, `clamp(30px, 4.2vw, 60px)`, line-height 1.18, letter-spacing -0.025em, max-width 1100px.
  > Every discipline I practice is, at its core, the same job: taking a *rough intent* and rendering it into something that feels inevitable. Code, cuts, prompts, translation — *same craft, different tools.*
- **Attribution** (50px below): 40×1px crimson bar, then "Aung Khant Hein — Studio manifesto, 2026" in JetBrains Mono 12px `--bone`, uppercased 0.1em tracking.

### 8. Process — `05 / How we work`

- Header: "Deliberate steps. *No surprises.* No mystery invoices."
- **Process list**: 5 rows, each a `grid-template-columns: 120px 1fr 2fr 60px` with 40px gap, 40px vertical padding, 1px `rgba(255,255,255,0.08)` top+bottom borders.
- **Hover state**: `padding-left: 20px` over 0.3s, title color shifts to crimson.
- Row anatomy:
  - **Col 1**: `/ Step 01` — JetBrains Mono 12px `--ash`, 0.15em tracking.
  - **Col 2**: Title — Fraunces 400 34px, -0.02em tracking, line-height 1.1.
  - **Col 3**: Description — 15px `--bone`, 1.6 line-height, max-width 520px.
  - **Col 4**: `→` — Fraunces 24px `--ash`, justify-self end.

- Mobile: collapses to `60px 1fr` grid, hides description + arrow, title 24px.

**Five steps (exact copy):**
1. **Brief & alignment** — A 45-minute call. I ask more questions than you expect. You leave with a written brief, a scope, and a fixed quote.
2. **Strategy & direction** — Before I touch the tools, I write the plan. Moodboards, prompt drafts, wireframes, or edit outlines — whichever fits.
3. **Build in daylight** — You get access to a shared workspace with daily progress logs. No waiting, no wondering, no black boxes.
4. **Two rounds of revisions** — Focused, structured feedback. Not endless. Not vague. We tune what needs tuning and we ship.
5. **Launch & handover** — Everything documented. Everything transferable. Two weeks of post-launch support included by default.

### 9. Contact — `06 / Contact`

- 180px top / 120px bottom padding, `text-align: center`.
- **Background glow**: absolute-centered 900×500px radial `rgba(230,57,70,0.28) → transparent`, 80px blur.
- Section number line, centered: `06 / Contact  ·  Let's build`.
- **Contact title**: Fraunces 300, `clamp(52px, 9vw, 148px)`, line-height 0.92, letter-spacing -0.035em:
  > Have a project<br>worth *obsessing over?*
- **Contact copy** (below): 17px `--bone`, 1.65 line-height, max-width 560px, 60px bottom margin.
  > I take on a small number of engagements each quarter — so that every one gets the attention it deserves. Tell me what you're building; I'll tell you honestly whether I'm the right person to help.
- **Email link** (`.contact-mail`): Fraunces 400 `clamp(24px, 3vw, 40px)`, letter-spacing -0.01em, 1px crimson bottom border, 6px padding-bottom, 16px gap to a 24×24px arrow icon. Hover: color → crimson. Points to `mailto:blackpearl101206@gmail.com`.
- **Socials strip** (90px above): 5 items (Instagram, LinkedIn, GitHub, Behance, Read.cv), 40px gap, JetBrains Mono 12px uppercase 0.15em, `--bone`. Hover: crimson + appearing `↗` glyph that translates (2px, -2px).

### 10. Design system appendix

Documented directly in the page as a reference for future contributors. Contains a swatch grid of the 7 core colors and 3 typographic samples with metadata (weight, size, tracking). Developers can strip this block for production if not needed publicly.

### 11. Footer

- 40px vertical padding, 1px `rgba(255,255,255,0.08)` top border.
- Flex row, space-between, JetBrains Mono 11px `--ash` uppercase 0.12em:
  - `© MMXXVI · Aung Khant Hein Studio`
  - `Handcrafted in HTML · No template used`
  - `● All systems operational` (green dot)

---

## Interactions & Behavior

| Interaction | Element | Duration | Easing | Property |
|---|---|---|---|---|
| Cursor lag | `.cursor` | continuous | 0.22 lerp per frame | transform |
| Cursor grow | on hover of `a, button, .service, .project, .process-item` | 0.25s | ease | width/height/bg |
| Caret blink | `.roles .role-slot::after` | 1s | steps(2) infinite | opacity |
| Typewriter type | `#roleSlot` | 40ms/char | linear | textContent |
| Typewriter erase | `#roleSlot` | 22ms/char | linear | textContent |
| Role pause between | — | 2200ms | — | — |
| Marquee scroll | `.marquee-track` | 40s | linear infinite | translateX |
| Nav CTA pulse dot | `.nav-cta .pulse` | 1.6s | ease-in-out infinite | opacity |
| Service card top-line | `.service::before` | 0.5s | cubic-bezier(.7,0,.3,1) | width |
| Service card bg swap | `.service:hover` | 0.4s | — | background |
| Service icon fill | `.service:hover .service-icon` | 0.3s | — | bg + border |
| Project card lift | `.project:hover` | 0.5s | cubic-bezier(.2,.9,.3,1) | transform |
| Project arrow spin | `.project:hover .arrow` | 0.3s | — | transform (rotate -45), bg, border |
| `viz-orb` float | in project card | 8s | ease-in-out infinite | transform |
| Process row slide | `.process-item:hover` | 0.3s | — | padding-left + title color |
| Button primary lift | `.btn-primary:hover` | 0.3s | — | translateY(-2px), bg, shadow |
| Scroll reveal | all `.service, .project, .process-item, .stat-num` | 0.8s | cubic-bezier(.2,.9,.3,1) | opacity 0→1, translateY 24→0px |
| Smooth anchor scroll | `html` | native | native | scroll-behavior: smooth |

**Scroll reveal**: IntersectionObserver, threshold 0.1. On intersect, remove initial opacity 0 / translateY(24px).

**Nav anchor targets**: `#about`, `#arsenal`, `#work`, `#process`, `#contact`.

**Responsive breakpoints**:
- `max-width: 900px` — hero grid collapses; about grid collapses; work grid collapses to 1 column.
- `max-width: 820px` — nav links hide (build a hamburger + drawer for production).
- `max-width: 800px` — arsenal grid → 1 column; process rows simplify; system grid → 1 column.
- `max-width: 720px` — section headers collapse to 1 column; section padding drops to 90px.

**Cursor accessibility**: on `@media (hover: none)`, cursor is hidden and default cursor is restored. Also consider hiding the custom cursor when `prefers-reduced-motion: reduce`.

**Reduced motion**: not currently implemented in the prototype. In production, wrap marquee, float, typewriter, and pulse animations in `@media (prefers-reduced-motion: no-preference)` and provide static fallbacks.

---

## State Management

Minimal — this is a marketing site.

- `roleIndex` — current role in the hero typewriter cycle (integer, mod 5).
- `cursorPosition` — `{tx, ty}` target + `{cx, cy}` lerped current position, updated every rAF.
- `intersectionObserved` — implicit via IntersectionObserver, no explicit state.

No data fetching. No forms with server actions. The contact CTA is a `mailto:` link.

Future considerations (not in scope for MVP):
- Case-study detail pages for the 6 project cards (currently `href="#"`).
- Contact form with server action (Resend, Postmark) as an alternative to `mailto:`.
- CMS integration for projects list (Sanity, Contentlayer).

---

## Design Tokens

### Colors

```css
--obsidian:      #0A0A0B;   /* Primary background */
--char:          #131316;   /* Section-level surface */
--graphite:      #1A1A1C;   /* Cards / surfaces */
--smoke:         #2A2A2E;   /* Borders (heavy) */
--ash:           #55555C;   /* Muted UI text */
--bone:          #C9C7C0;   /* Body text */
--paper:         #F5F5F0;   /* Primary text / bg-on-dark */
--crimson:       #E63946;   /* Primary accent */
--crimson-deep:  #B31E2A;   /* Hover / pressed */
--ember:         #FF5A67;   /* Button hover */
--gold:          #E9B949;   /* Secondary accent */
```

Semantic overlays (used throughout):
- `rgba(255,255,255,0.05)` — hairline borders
- `rgba(255,255,255,0.08)` — section dividers, card borders
- `rgba(255,255,255,0.15)` — button ghost borders
- `rgba(0,0,0,0.55)` — nav backdrop
- `rgba(0,0,0,0.85)` — project card gradient base
- `rgba(230,57,70,0.28)` / `0.35` / `0.55` / `0.7` — crimson glow layers

### Typography

Google Fonts imports:
```
Fraunces (opsz 9..144, weights 300/400/500/600/700, roman + italic)
Space Grotesk (weights 300/400/500/600/700)
JetBrains Mono (weights 400/500)
```

CSS vars:
```css
--font-display: 'Fraunces', Georgia, serif;
--font-sans:    'Space Grotesk', -apple-system, sans-serif;
--font-body:    'Space Grotesk';
--font-mono:    'JetBrains Mono', ui-monospace, monospace;
```

Type scale (all with letter-spacing/line-height noted):
| Role | Font | Weight | Size | LH | Tracking |
|---|---|---|---|---|---|
| Hero H1 | Fraunces | 300 | clamp(48, 7.4vw, 118)px | 0.92 | -0.035em |
| Contact H2 | Fraunces | 300 | clamp(52, 9vw, 148)px | 0.92 | -0.035em |
| Section title | Fraunces | 300 | clamp(36, 5vw, 72)px | 1.02 | -0.03em |
| Philosophy quote | Fraunces | 300 | clamp(30, 4.2vw, 60)px | 1.18 | -0.025em |
| About lede | Fraunces | 300 | 32px | 1.25 | -0.015em |
| Card H3 | Fraunces | 400 | 32px | 1.1 | -0.02em |
| Process title | Fraunces | 400 | 34px | 1.1 | -0.02em |
| Stat number | Fraunces | 300 | 56px | 1 | -0.03em |
| Project title | Fraunces | 400 | 22px | 1.15 | -0.01em |
| Contact mail | Fraunces | 400 | clamp(24, 3vw, 40)px | — | -0.01em |
| Body large | Space Grotesk | 400 | 17px | 1.65 | — |
| Body | Space Grotesk | 400 | 16px | 1.75 | — |
| Body small | Space Grotesk | 400 | 15px | 1.65 | — |
| Nav link | Space Grotesk | 400 | 13.5px | — | — |
| Bold body | Space Grotesk | 500 | inherits | — | — |
| Mono eyebrow | JetBrains Mono | 400 | 12px | — | 0.15em uppercase |
| Mono label sm | JetBrains Mono | 400 | 11px | — | 0.12em uppercase |
| Mono tag | JetBrains Mono | 400 | 10.5px | — | 0.05em uppercase |
| Mono corner HUD | JetBrains Mono | 400 | 10px | — | 0.15em |

Italic-crimson accent (`<em>`) is used across all Fraunces display sizes — always keep italics + crimson colour paired for emphasis.

### Spacing

Base unit **8px**. Common values in use:
- 4, 6, 8, 10, 12, 14, 16, 22, 24, 26, 28, 30, 32, 34, 40, 44, 50, 60, 80, 90, 100, 120, 140, 160, 180 (all px).
- Section vertical padding: **140px** desktop / **90px** mobile.
- Page horizontal padding: **40px** desktop / **22px** mobile.
- Max container width: **1360px**.

### Border radius

- **4px** — badges, small chips
- **6px** — project cards, portrait frame
- **8px** — arsenal grid container
- **50%** — icons, cursor, pulse dot, project arrow
- **999px** — pills (nav CTA, buttons, tags)

### Shadow

```css
/* Portrait frame */
box-shadow: 0 40px 80px -20px rgba(0,0,0,0.8), 0 0 0 1px rgba(255,255,255,0.06);
/* Portrait badge */
box-shadow: 0 20px 40px -10px rgba(0,0,0,0.6);
/* Primary button */
box-shadow: 0 12px 40px -8px rgba(230,57,70,0.55);
/* Primary button hover */
box-shadow: 0 16px 48px -6px rgba(230,57,70,0.7);
/* Logo dot glow */
box-shadow: 0 0 12px var(--crimson);
/* Pulse dot glow */
box-shadow: 0 0 8px #4ade80;
/* Orb glow */
box-shadow: 0 0 80px rgba(230,57,70,0.5);
/* Triangle drop-shadow (filter) */
filter: drop-shadow(0 0 40px rgba(230,57,70,0.4));
```

Effects:
- **Backdrop blur (nav)**: `blur(14px) saturate(140%)`.
- **Film grain**: SVG feTurbulence, `baseFrequency=0.9`, 3 octaves, `opacity: 0.06`, `mix-blend-mode: overlay`, fixed full-viewport, `z-index: 9999`.
- **Cursor**: `mix-blend-mode: difference`.

---

## Assets

- **`assets/portrait.jpg`** — 45KB JPEG portrait of Aung Khant Hein. Dramatic crimson studio lighting on dark background, 4:5 aspect. This asset defines the site's colour palette (the crimson accent is drawn from the lighting) — do not swap for a differently-lit photo without re-tuning the palette. Located in `assets/portrait.jpg`.
- **Icons** — All 4 service icons and the arrow/envelope icons are inline SVG (24×24 viewbox, 1.6–1.8 stroke, `currentColor`). No icon library required. Copy them from the source HTML or substitute with equivalents from Lucide/Heroicons in production.
- **Film grain** — Inline SVG data URI, no external asset.
- **Fonts** — Loaded from Google Fonts CDN. In production use `next/font` or self-host with `.woff2` files for performance.

---

## Files

- **`Portfolio.html`** — the complete design prototype. Single self-contained file. All CSS is in the `<style>` block in `<head>`; all JS is in the `<script>` block before `</body>`. Structural landmarks:
  - Lines ~11–860: CSS (design tokens + all component styles).
  - Lines ~890–920: nav.
  - Lines ~921–990: hero.
  - Lines ~995–1010: marquee.
  - Lines ~1014–1060: about.
  - Lines ~1064–1160: arsenal.
  - Lines ~1164–1280: work grid.
  - Lines ~1283–1300: philosophy.
  - Lines ~1305–1345: process.
  - Lines ~1349–1385: contact.
  - Lines ~1390–1445: design-system appendix.
  - Lines ~1448–1460: footer.
  - Lines ~1462–1505: scripts (cursor, typewriter, IntersectionObserver).

- **`assets/portrait.jpg`** — the hero portrait image.

Read `Portfolio.html` end-to-end before starting implementation. All motion timings, exact class combinations for the asymmetric work grid, and full copy strings are authoritative there.
