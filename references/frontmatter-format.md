# Frontmatter Format Spec

The newer, token-first DESIGN.md format. Used by ~60% of `awesome-design-md` (Linear, Notion, Claude, Apple, Nike, Figma, Framer, Pinterest, Cursor, Cohere, Mistral, Bugatti, Ferrari, Renault, etc.).

## File shape

```
---
version: alpha
name: <Brand Name>
description: "<One paragraph that defines canvas, voltage, type voice, and what makes this brand different.>"

colors:
  <semantic-name>: "<#hex>"
  ...

typography:
  <role>:
    fontFamily: <stack or proprietary name>
    fontSize: <px>
    fontWeight: <int>
    lineHeight: <number>
    letterSpacing: <px>
  ...

rounded:
  xs: 4px
  ...
  pill: 9999px
  full: 9999px

spacing:
  xxs: 4px
  ...
  section: 96px

components:
  <name>:
    backgroundColor: "{colors.X}"
    textColor: "{colors.Y}"
    typography: "{typography.Z}"
    rounded: "{rounded.K}"
    padding: <values>
    height: <px>     # optional
  ...
---

## Overview
...

## Colors
...

## Typography
...

## Layout
...

## Elevation & Depth
...

## Shapes
...

## Components
...

## Do's and Don'ts
...

## Responsive Behavior
...

## Iteration Guide
...

## Known Gaps
...
```

## Frontmatter (YAML) — section-by-section

### `version`, `name`, `description`
- `version: alpha` — corpus convention. Don't bikeshed.
- `name: <Brand>` — proper-cased brand name. Examples: `Linear`, `Stripe`, `Claude`, `Notion`, `Apple`.
- `description:` — ONE paragraph (3–6 sentences). Must contain: canvas color (named role + hex), brand primary (named role + hex), display & body font families, the one thing that makes this brand visually unmistakable. This paragraph is what an LLM may read in isolation if everything else is truncated, so it must stand alone.

### `colors:`
Flat dictionary of `semantic-name: "#hex"`. Names use kebab-case role nouns, NOT literal color names. The complete vocabulary, in order of typical appearance:

```yaml
# Brand
primary: "<hex>"            # the one signature accent
primary-hover: "<hex>"      # optional
primary-active: "<hex>"     # optional
primary-focus: "<hex>"      # optional, focus rings
primary-disabled: "<hex>"   # optional
on-primary: "<hex>"         # text guaranteed legible on primary

# Text
ink: "<hex>"                # default headline color
ink-muted: "<hex>"          # secondary text
ink-subtle: "<hex>"         # tertiary text / footers
ink-tertiary: "<hex>"       # quaternary, disabled, footnotes
body: "<hex>"               # paragraph color (if distinct from ink)
body-strong: "<hex>"        # emphasized body
muted: "<hex>"              # captions

# Surface (page + cards)
canvas: "<hex>"             # page-level background
surface-soft: "<hex>"       # very light section divider
surface-1: "<hex>"          # one step above canvas
surface-2: "<hex>"          # two steps above
surface-3: "<hex>"          # three (rare)
surface-4: "<hex>"          # four (very rare)
surface-card: "<hex>"       # alternative naming
surface-dark: "<hex>"       # if mixed-mode brand has a dark inverse
surface-dark-elevated: "<hex>"
inverse-canvas: "<hex>"     # if light/dark inversion is documented
inverse-ink: "<hex>"

# Borders / hairlines
hairline: "<hex>"
hairline-strong: "<hex>"
hairline-soft: "<hex>"

# Semantic
success: "<hex>"
warning: "<hex>"
error: "<hex>"
info: "<hex>"               # optional
semantic-overlay: "<hex>"   # modal scrim

# Accents (decorative, sparing)
accent-<name>: "<hex>"      # e.g. accent-teal, accent-amber, accent-pink
brand-<name>: "<hex>"       # branded sub-categories (e.g. brand-navy)
card-tint-<name>: "<hex>"   # tinted card surfaces (e.g. card-tint-peach)
```

Rules:
- Only include tokens the brand actually uses. A monochrome system has no `accent-*`. A site without semantics has no `success`. Don't pad.
- The single chromatic brand color is always `primary`. If the brand has two equally-weighted accents (rare), name the second one `accent-<role>`, never `secondary` (`secondary` reads as "lesser primary").
- Surface ladder names go `canvas` → `surface-1` → `surface-2` … in increasing lift. Always start at `canvas`.

### `typography:`
Each role is its own block with `fontFamily`, `fontSize`, `fontWeight`, `lineHeight`, `letterSpacing`. Standard role catalog:

```yaml
display-xl:    # largest hero (60–96px)
display-lg:    # secondary hero (40–64px)
display-md:    # sub-section heads (32–48px)
display-sm:    # smaller display (24–32px)
headline:      # 24–28px section opener
card-title:    # ~20–24px
title-lg:      # ~22px
title-md:      # ~18px
title-sm:      # ~16px
subhead:       # lead paragraph
body-lg:       # 18px lead body
body-md:       # 16px default body (sometimes just `body`)
body-sm:       # 14px small body
caption:       # 12–13px metadata
caption-uppercase:  # 12px uppercase eyebrow
eyebrow:       # 13px section taxonomy
button:        # button labels
nav-link:      # navigation items
mono / code:   # monospace
```

Rules:
- Skip roles the brand doesn't use. If there's no eyebrow on the site, don't invent one.
- Letter-spacing is critical at display sizes. Many brands run aggressive negative tracking (Linear -3px @ 80px, Vercel -2.4 to -2.88, Stripe -1.4 @ 56px). Capture exact values.
- Line-height: tight (1.0–1.2) for display, loose (1.4–1.6) for body. Don't round to "normal" — be numeric.
- For proprietary fonts, list the proprietary name first, then the public fallback (e.g. `"Copernicus, Tiempos Headline, serif"` or `Linear Display`).

### `rounded:`
```yaml
xs: 4px
sm: 6px
md: 8px       # default for buttons + inputs
lg: 12px      # default for cards
xl: 16px      # for product mockup tiles, hero illustrations
xxl: 24px     # rare, oversized CTA banners
pill: 9999px
full: 9999px  # circles (avatars)
```
Skip rungs the brand doesn't use. Some brands max out at 8px (Stripe, conservative); others go to 24px (warm/playful brands).

### `spacing:`
```yaml
xxs: 4px
xs: 8px
sm: 12px
md: 16px
lg: 24px
xl: 32px
xxl: 48px
section: 96px   # outer rhythm between major bands; sometimes 64px or 80px
```
Most modern marketing surfaces land at 96px section padding. Smaller editorial sites use 64–80px.

### `components:`
Dictionary of named components. Each component is a flat block referencing tokens via `{token.refs}`:

```yaml
button-primary:
  backgroundColor: "{colors.primary}"
  textColor: "{colors.on-primary}"
  typography: "{typography.button}"
  rounded: "{rounded.md}"
  padding: 8px 14px
  height: 40px
```

State variants are separate entries with the suffix:
- `-hover`, `-active`, `-pressed`, `-focused`, `-disabled`, `-selected`

Standard component catalog (include only what the brand actually has):

```
button-primary, button-primary-hover, button-primary-pressed, button-primary-disabled
button-secondary, button-secondary-on-dark
button-tertiary, button-ghost, button-inverse
button-icon-circular
text-link
top-nav, footer
hero-band, hero-illustration-card
feature-card, pricing-card, pricing-card-featured, testimonial-card
product-screenshot-card, product-mockup-card, product-mockup-card-dark
code-window-card
customer-logo-tile
text-input, text-input-focused
pricing-tab-default, pricing-tab-selected
status-badge, badge-pill, badge-coral
cta-banner, cta-band-coral, cta-band-dark
changelog-row
cookie-consent-card
connector-tile
category-tab, category-tab-active
```

Rules:
- Component values are tokens, not literals. `backgroundColor: "{colors.primary}"` not `backgroundColor: "#5e6ad2"`. Padding/height/size can be raw values since they're rarely tokenized.
- If a component takes a 1px border, mention it in the prose; YAML doesn't have a `border` field convention.
- Order: nav → buttons → cards → inputs → badges → CTA bands → footer is the canonical reading order.

## Markdown body — section-by-section

After the closing `---`, the prose sections appear in this order:

### `## Overview`
2–4 paragraphs (~150–400 words) plus a `**Key Characteristics:**` bullet list of 6–9 items. Re-state the canvas + voltage from the description, but with more depth: how surfaces alternate, what the section rhythm is, what dominates the page (product UI? photography? code mockups?), what the typographic voice is. End with the bullet list — these are agent-quotable one-liners.

### `## Colors`
Group by role with `### Brand & Accent`, `### Surface`, `### Text`, `### Semantic`. Each color line is:
```
- **Display Name** (`{colors.token}` — #hex): What it's used for, with a specific page-or-component reference.
```
Example:
```
- **Lavender-Blue** (`{colors.primary}` — #5e6ad2): The signature Linear accent — primary CTA, brand mark, link emphasis.
```
Always cite at least one place the color appears.

### `## Typography`
Three subsections:

**`### Font Family`** — list each family with name + fallback stack + role (display vs text vs mono). One paragraph after the list explaining how the families relate ("The marketing surface treats Display and Text as one continuous voice; the family change is silent.").

**`### Hierarchy`** — a markdown table:
| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `{typography.display-xl}` | 80px | 600 | 1.05 | -3.0px | Largest hero headline |

Every typography token in the YAML must appear in the table.

**`### Principles`** — bullet list of typographic non-negotiables ("Aggressive negative tracking on display", "Single voice from display to body", "Eyebrow uses positive tracking", "Mono only in code contexts").

**`### Note on Font Substitutes`** (optional but recommended for proprietary faces) — name open-source replacements (Inter, Geist Sans, JetBrains Mono, Cormorant Garamond, EB Garamond, etc.).

### `## Layout`
Three subsections:

**`### Spacing System`** — base unit + token list with values + notes on which paddings are used where ("Card interior padding: `{spacing.lg}` 24px on feature/pricing cards").

**`### Grid & Container`** — max content width, column counts, what grids appear at what breakpoints (e.g. "Card grids are 3-up at desktop, 2-up at tablet, 1-up at mobile.").

**`### Whitespace Philosophy`** — one paragraph on whether whitespace is generous (Apple, Tesla), measured (Stripe), or replaced by surface-lift on dark (Linear).

### `## Elevation & Depth`
A markdown table:
| Level | Treatment | Use |
|---|---|---|
| 0 (flat) | No shadow, no border | Default body |
| 1 (charcoal lift) | `{colors.surface-1}` background, 1px `{colors.hairline}` | Default cards |
| ... | ... | ... |

After the table, a paragraph on the brand's depth philosophy (shadow vs surface-lift vs hairline). A `### Decorative Depth` subsection describes anything else that adds depth (gradients, scrim, edge-highlight, product UI screenshots).

### `## Shapes`
**`### Border Radius Scale`** — table mapping each `{rounded.X}` token to a value and a use.

**`### Photography & Illustration Geometry`** (or `### Photography & Illustrations`) — one paragraph on how images are framed: edge-to-edge? in `{rounded.xl}` cards? avatars at `{rounded.full}`? line-art? The answer can be "no decorative imagery" — say so.

### `## Components`
Group with `### Top Navigation`, `### Buttons`, `### Cards & Containers`, `### Inputs & Forms`, `### Tags / Badges`, `### Tab / Filter`, `### Status & X`, `### CTA / Footer`. Each component gets a paragraph (3–6 lines) tying together its tokens and explaining where on the site it appears.

Format per component:
```
**`component-name`** — One-sentence description.
- Background `{colors.X}`, text `{colors.Y}`, type `{typography.Z}`, rounded `{rounded.K}`, padding ...
- Variant: ...
```

### `## Do's and Don'ts`
Two subsections, `### Do` and `### Don't`. Each is a bulleted list of 6–9 items. The Don'ts are at least as valuable as the Dos — they tell the agent what NOT to default to.

Anti-patterns to consider for the Don't list:
- Don't introduce a second chromatic accent.
- Don't pill-round CTAs (or DO pill-round, brand-dependent).
- Don't use pure black `#000000` as canvas (when the brand uses a tinted near-black).
- Don't bold display weight (when brand uses light or regular).
- Don't use neutral gray shadows (when brand uses tinted shadows).
- Don't ship light mode (or dark mode) when the brand has only one.

### `## Responsive Behavior`
**`### Breakpoints`** — table of named breakpoints + width + key changes.

**`### Touch Targets`** — minimum tap heights for buttons, pills, inputs.

**`### Collapsing Strategy`** — which grids reduce columns at which breakpoints; how nav collapses; how display type scales down.

**`### Image Behavior`** — how product screenshots, illustrations, photography respond.

### `## Iteration Guide`
Numbered list (5–8 items) of workflow rules for an agent extending the system: "Focus on ONE component at a time," "Variants live as separate entries," "Use `{token.refs}` everywhere — never inline hex," "Display headlines stay <font> at <weight>; the split is unbreakable."

### `## Known Gaps`
Bulleted list of what was NOT extracted, what's proprietary, what's out of scope. Honesty here prevents the agent from hallucinating.

Common gaps:
- Proprietary fonts not publicly distributed (with substitutes already named in the typography section).
- Form validation states beyond focused.
- Light mode (or dark mode) not shipped on the source.
- Animation / transition timings.
- Product surfaces (in-app UI) vs marketing surface — usually only marketing is captured.

## Reference: real frontmatter-format files in `awesome-design-md`

When in doubt, mimic the voice and structure of:
- `linear.app/DESIGN.md` — dark, surface-ladder, restrained
- `claude/DESIGN.md` — warm cream + coral, editorial slab serif
- `apple/DESIGN.md` — photography-first, minimal chrome
- `notion/DESIGN.md` — illustration-rich, multi-tier surfaces
- `nike/DESIGN.md` — typographic contrast, photography commerce
