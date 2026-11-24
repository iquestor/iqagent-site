---
name: iQagent sites (iqagent.com and software.iqagent.com)
description: A plain-spoken industrial look: steel-navy bars, signal-amber actions, system fonts, real product photos.
colors:
  signal-amber: "#f5a300"
  amber-bright: "#ffb52e"
  steel-navy: "#13293d"
  navy-lift: "#1d3f5e"
  ink-navy: "#14212e"
  steel-blue: "#1f5f94"
  slate-muted: "#51606f"
  rule-grey: "#d9e0e7"
  page-white: "#ffffff"
  mist: "#f3f6f9"
  placeholder-yellow: "#fff3b0"
  placeholder-ink: "#5a4a00"
typography:
  display:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
    fontSize: "2.3rem"
    fontWeight: 700
    lineHeight: 1.2
  headline:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
    fontSize: "1.7rem"
    fontWeight: 700
    lineHeight: 1.25
  title:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
    fontSize: "1.1rem"
    fontWeight: 700
    lineHeight: 1.6
  body:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
    fontSize: "1rem"
    fontWeight: 400
    lineHeight: 1.6
  label:
    fontFamily: "-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Helvetica, Arial, sans-serif"
    fontSize: "0.88rem"
    fontWeight: 400
    lineHeight: 1.6
rounded:
  sm: "5px"
  md: "8px"
  lg: "10px"
  pill: "999px"
spacing:
  xs: "8px"
  sm: "12px"
  md: "20px"
  lg: "28px"
  xl: "56px"
components:
  button-primary:
    backgroundColor: "{colors.signal-amber}"
    textColor: "{colors.ink-navy}"
    rounded: "{rounded.md}"
    padding: "12px 22px"
  button-primary-hover:
    backgroundColor: "{colors.amber-bright}"
  button-ghost:
    backgroundColor: "transparent"
    textColor: "{colors.page-white}"
    rounded: "{rounded.md}"
    padding: "12px 22px"
  card:
    backgroundColor: "{colors.page-white}"
    textColor: "{colors.ink-navy}"
    rounded: "{rounded.lg}"
    padding: "20px"
  site-header:
    backgroundColor: "{colors.steel-navy}"
    textColor: "{colors.page-white}"
    height: "60px"
---

# Design System: iQagent sites

**Scope.** This file describes `main/css/style.css` (iqagent.com), which now uses the steel-navy and signal-amber palette below. `software/css/style.css` (software.iqagent.com) is the same system with the earlier orange (#c2410c) and charcoal (#20262d) palette and the older hero layout. It has not been updated. NOTES.md says not to change `iqagent-software` until Paddle finishes verifying the owner's ID. Until then the two sites differ in color.

## Overview

**Creative North Star: "The Plant-Floor Placard"**

The sites look like equipment signage: a deep steel-navy bar across the top, signal amber where something needs attention, and plain dark-on-white text on a clean page. There is no decoration for its own sake. Real product photos and real numbers carry the visual weight, and the type is the operating system's own font. Amber reads as an andon or warning lamp, and the navy echoes the blue motors in the hero photo.

The density is moderate: a 1240px container on the brand site (760px for legal and contact text), 56px section padding, and white and cool-mist sections alternating. The hero and the "Less time hunting" section mirror each other, with the image on the right and then on the left, so the page zigzags. Amber is used for actions and for counted or chosen things (step markers, the featured plan). Mood was not specified by the owner, so this describes what the CSS does and not a stated aspiration.

**Key Characteristics:**
- Steel-navy header, hero and footer bands framing a light content area
- One accent, signal amber, with dark ink text on it
- System font stack, bold headings, regular body, no display face
- Flat cards with a 1px hairline border and a 10px corner; shadows only on photos and video
- Light and dark themes through `prefers-color-scheme`
- Loud yellow placeholders so unfinished copy cannot ship by accident

## Colors

A restrained palette: steel navy, white and cool mist for structure, one warm amber accent, and a muted slate for secondary text.

### Primary
- **Signal Amber** (#f5a300): the button fill, header underline, "agent" in the logo, step number discs and the featured-plan border. Text on it is always Ink Navy, never white.
- **Amber Bright** (#ffb52e): button hover.

### Secondary
- **Steel Blue** (#1f5f94): link color on light pages and the big numbers in the proof tiles. In dark mode links use a light steel blue (#7db8ee).

### Neutral
- **Steel Navy** (#13293d): header, footer, CTA band, and the start of the hero gradient.
- **Navy Lift** (#1d3f5e): the end of the hero gradient (160deg from steel navy).
- **Ink Navy** (#14212e): body text on light pages, and text on amber buttons.
- **Slate Muted** (#51606f): secondary text, captions, lead paragraphs, FAQ answers.
- **Rule Grey** (#d9e0e7): card borders, FAQ dividers, plan list dividers.
- **Page White** (#ffffff): the page and card background.
- **Mist** (#f3f6f9): alternating section background (`section.alt`).

### Status and utility
- **Placeholder Yellow** (#fff3b0) on **Placeholder Ink** (#5a4a00): draft banner and `.ph` spans, deliberately garish. It is a pale yellow and must stay clearly different from Signal Amber.

### Dark mode
Dark mode swaps the page to #0e1a26, alt sections to #13222f, text to #e8eef4, muted to #9fb0c0, rules to #223548 and the header to the page color. The amber accent is unchanged and links turn light steel blue (#7db8ee).

### Named Rules
**The One Voice Rule.** Amber is the only accent. It marks actions and counted or chosen things, not decoration.
**The Dark-on-Amber Rule.** Text on amber is Ink Navy. White on amber fails contrast.
**The Loud Placeholder Rule.** Unfinished copy is pale yellow. A page with any yellow like that on it is not ready to publish.

## Typography

**Font:** the system UI stack (-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif). No web fonts are loaded.

**Character:** neutral and quick, the look of a tool and not a brand magazine. Weight does the hierarchy: bold headings, regular body.

### Hierarchy
- **Display** (700, 2.3rem, 1.2; 1.8rem under 820px): the hero h1.
- **Headline** (700, 1.7rem, 1.25): section h2. The split section's h2 is 2rem (1.7rem under 820px).
- **Title** (700, 1.1rem; 1.3rem for product cards, 1.05rem for feature items): card and feature headings.
- **Body** (400, 16px, 1.6): all running text. Lead paragraphs are 1.05rem in Slate Muted, capped at 720px. The split section's paragraph is 1.15rem.
- **Label** (400, 0.88 to 0.97rem): captions, fine print, nav links (0.95rem), card text (0.97rem).
- **Stat** (700, 2.2rem, Steel Blue): the proof numbers on the home page. Prices are 2rem bold.

### Named Rules
**The No-Web-Font Rule.** The system stack is a constraint of the current design, not an oversight. Changing it is a deliberate redesign decision.

## Layout

Single-column flow of full-width sections inside a centered container: 1240px max (header, hero and every section share it), 760px for the narrow variant used by legal and contact text. 20px side padding. Sections are 56px tall top and bottom and alternate white and mist.

The hero is a two-column grid (.85fr text / 1.15fr image, 48px gap) that stacks under 820px. The "Less time hunting for information" section is a 1fr / 1fr split with the image on the left and text on the right (56px gap). On phones the text comes first and the image second. Cards use `repeat(auto-fit, minmax(...))`: 240px, plans 230px, products 300px, stats 180px, screenshots 420px. Header is sticky at 60px with wrapping nav on small screens.

Rhythm: gaps of 20px between cards, 28px above grids, 40 to 56px in hero and split grids.

## Elevation & Depth

Mostly flat. Cards, plans and steps have no shadow, only a 1px Rule Grey border. Depth shows up only on media: photos carry a large soft shadow (0 10px 30px at 25% black) and the video embed carries a similar one.

### Shadow Vocabulary
- **Photo** (`box-shadow: 0 10px 30px rgba(0,0,0,.25)`): images on both sites.
- **Hero screenshot, software** (`0 24px 60px rgba(0,0,0,.45), 0 2px 6px rgba(0,0,0,.3)`): the large hero image on the software site only.

### Named Rules
**The Flat-Cards Rule.** Cards are outlined, not lifted. Shadows belong to photos and video.

## Shapes

Gently rounded. Cards, photos and fields use a 10px corner; buttons use 8px; the speed-chart bars (software site) use 5px; the featured-plan badge is a full pill. Tip callouts have a flat left edge (4px amber bar) and rounded right corners. Step numbers are 30px circles. Borders are 1px Rule Grey, with 2px for the featured plan (amber) and ghost buttons (current color).

## Components

### Buttons
- **Shape:** 8px corners, bold (600) label, 2px border.
- **Primary:** Signal Amber fill with Ink Navy text, 12px by 22px padding.
- **Hover:** background and border lighten to Amber Bright. No transform.
- **Ghost:** transparent with a current-color border; on the dark hero, white text and a faint white wash on hover.
- **Small:** 8px by 16px at 0.92rem. In the header nav the button is 7px by 14px.

### Header and navigation
- Sticky steel-navy bar, 60px minimum, with a 3px amber bottom line. The logo is bold white "iQ" plus a lighter amber "agent" span. Nav links are 0.95rem light grey that turn white and underline on hover, with an amber button for the demo call to action. On the brand site the nav reads iQagent · Other tools · Contact · Book a demo. Nav wraps onto its own row under 820px.

### Cards and containers
- **Corner:** 10px. **Background:** page color. **Border:** 1px Rule Grey. **Padding:** 20px (28px for product cards, 24px for pricing plans).
- Plans: the featured plan has a 2px amber border and, on the software site, a floating pill badge.

### Split feature
- A two-column section with a photo and a text block (h2, a larger paragraph and a primary button). Used once on the brand home page. The photo uses the standard photo treatment and keeps its natural 4:3 ratio.

### Steps
- Cards with a numbered 30px amber disc at left (Ink Navy numeral), text in Slate Muted.

### Proof stats
- Centered large bold number in Steel Blue with a muted caption beneath.

### FAQ
- Native `<details>` with a bold summary and Rule Grey dividers. No custom icon.

### Inputs (software buy form)
- 10px corner, 1px Rule Grey border, inherits font, 10px by 12px padding. Labels are bold at 0.95rem with a muted hint line. The CSS defines no focus style beyond the browser default.

### Media
- Photos: 1px border, 10px corner, soft shadow; on the software site a zoom-in cursor opens a lightbox dialog (80% black backdrop, 8px corner).
- Video: 16:9 embed, 10px corner, soft shadow, black fallback.

### CTA band
- Full-width steel-navy band with centered white text, a 1.25rem semibold line and a lighter sub-line.

## Do's and Don'ts

### Do:
- **Do** keep amber for actions and counted or chosen things (buttons, steps, featured option), with Ink Navy text on it.
- **Do** use the system font stack and bold weights for hierarchy.
- **Do** show real product photos and screenshots with the existing border, corner and shadow.
- **Do** alternate white and mist sections, keep 56px section padding, and keep sections on the shared 1240px container.
- **Do** keep both light and dark themes working (they use the same variables).
- **Do** make unfinished copy pale yellow (`.ph`, `.draft-banner`) so it is obvious.

### Don't:
- **Don't** put white text on amber; it fails contrast.
- **Don't** add a second accent color or decorative gradients; the only gradient is the navy hero.
- **Don't** put shadows on cards. They belong to photos and video.
- **Don't** introduce web fonts without treating it as a redesign decision.
- **Don't** add stock photography, invented logos, customer names or testimonials. PRODUCT.md says none exist.
- **Don't** let the two sites' CSS drift further apart without deciding whether they should share one file.
