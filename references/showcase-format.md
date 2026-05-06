# Showcase HTML — Format Spec

Every DESIGN.md ships with a parallel `design-showcase.html` — a single-file, double-clickable visual rendering of the brand's tokens. The showcase is what the user opens to *see* the system without running a server, parsing markdown, or installing tooling.

The file lives next to the DESIGN.md (same folder), is self-contained (no fetch, no JS deps beyond Google Fonts via CDN), and is generated alongside the DESIGN.md every time a new one is authored.

The template lives at `templates/showcase.html` — a complete working scaffold with neutral placeholder content (a generic "BRAND NAME" with a cyan-blue voltage on a near-black canvas). It renders end-to-end as a generic example so you can verify structure before adapting; your job in Phase 6 is to substitute every BRAND-SPECIFIC marker for the new brand's actual tokens, copy, and assets.

## What the showcase contains

Nine numbered sections. Some are universal; some are conditional on brand category.

| # | Section | Universal? | Notes |
|---|---|---|---|
| — | Top nav + hero | ✓ | Brand name, stripe motif, hero copy, two CTAs, canvas demo with brand mark |
| 00 | Logo lockup | ✓ | Dark + light + mono-white + mono-black variants. Skip if no logo provided. |
| 01 | Color palette | ✓ | Auto-grouped: Brand voltage / Surface / Text / Borders+Semantic. Includes proportion bar. |
| 02 | Typography scale | ✓ | One row per role, mono-spec on left, rendered specimen on right. |
| 03 | Button variants | ✓ | Primary states, secondary, ghost, icon, text-link. |
| 04 | Inputs · Badges | ✓ | Default/focused/error inputs + badge variants. |
| 05 | Cards | ✓ | Feature cards, pricing tier with featured glow, testimonial. Adapt copy to brand category. |
| 06 | Product UI primitives | conditional | Only for software/tools brands. Replace with brand-relevant primitives or skip. |
| 07 | Elevation & depth | ✓ | Five levels — flat → surface lift → hover → spotlight → focus ring. |
| 08 | Shapes & spacing | ✓ | Border-radius scale + spacing scale (rendered as bars). |
| 09 | Do's & Don'ts | ✓ | Two-column rules pulled from DESIGN.md prose. |

## How to adapt the template

Every place you must change for a new brand falls into one of these categories. Search the template for the `BRAND-SPECIFIC` HTML comments — they mark the spots that need substitution.

### 1) `:root` CSS variables — direct substitution from frontmatter

Every variable in `:root` maps 1:1 to a token in the DESIGN.md frontmatter. Replace the placeholder hex values with the new brand's tokens.

| `:root` variable | Frontmatter token | Notes |
|---|---|---|
| `--primary` | `colors.primary` | The brand voltage |
| `--primary-hover` / `--primary-active` / `--primary-disabled` | same | If the brand omits these, derive (lighter / darker / desaturated) |
| `--on-primary` | `colors.on-primary` | Text on primary surface |
| `--canvas` | `colors.canvas` | Page floor |
| `--surface-1` … `--surface-3` | same | Drop rungs the brand doesn't define |
| `--ink` / `--ink-muted` / `--ink-subtle` / `--ink-tertiary` | same | Map to whatever ink scale the brand uses |
| `--hairline` / `--hairline-strong` | same | |
| `--success` / `--warning` / `--error` | same | If the brand has no semantic palette, keep template defaults and note in Known Gaps |
| `--gradient-from` / `--gradient-to` | `colors.gradient-from` / `gradient-to` | Only if the brand defines a gradient — otherwise remove the `signature-stripe` use |
| `--r-xs` … `--r-pill` | `rounded.*` | |
| `--xxs` … `--hero` | `spacing.*` | |
| `--display` / `--body` / `--mono` | derived from `typography.display-xl.fontFamily` / `typography.body.fontFamily` / `typography.mono.fontFamily` | Use the first family in the stack |

### 2) Google Fonts URL — rebuild from typography families

Replace the `<link href="https://fonts.googleapis.com/css2?…">` URL using the brand's display + body + mono family names with the weights actually used in the typography section.

Example pattern:
```
https://fonts.googleapis.com/css2?family=<Display+Family>:wght@<weights>&family=<Body+Family>:wght@<weights>&family=<Mono+Family>:wght@<weights>&display=swap
```

If the brand uses a proprietary font, fall back to the named open-source substitute from the DESIGN.md's "Note on Font Substitutes" section.

### 3) Logo SVG — brand mark

The template has a placeholder geometric mark (rounded square + concentric circle) drawn in inline SVG, repeated in:
- Hero canvas (large, 140px with primary glow)
- Logo lockup section (4 variants: dark / light / mono-white / mono-black)

**If the new brand provides a logo file:** Inline a simplified SVG version. Keep the same locations and the four-variant lockup.

**If no logo is provided:** Use a wordmark-only lockup (just the brand name in display family). Skip the symbol entirely. Remove the hero canvas symbol or replace with a typographic ornament.

### 4) Hero copy

Three places:
- `<h1>` — pattern: `Design system inspiration of <brand>` or a brand tagline if the manual provides one
- `<p class="lede">` — derived from the DESIGN.md `description` paragraph; trim to ~3 sentences
- Two `<button>` labels — `Discover <brand>` + `View DESIGN.md` (default), or replace with brand-specific CTAs

### 5) Section descriptions

Every numbered section has a `.sec-desc` paragraph below the title. Rewrite each in the brand's voice, pulling from the DESIGN.md prose. Don't reuse the template's placeholder wording.

### 6) Color swatches — repeat per token

Section 01 has four color groups (Brand voltage / Surface / Text / Borders+Semantic). Each group is a `.color-group` containing a `.swatch-grid` with 3–5 `.swatch` blocks.

For each color in the brand's `colors:` frontmatter, generate one `.swatch`:
```html
<div class="swatch">
  <div class="swatch-color" style="background:<HEX>"></div>
  <div class="swatch-meta">
    <div class="name"><TOKEN_NAME_UPPERCASE></div>
    <div class="hex"><HEX></div>
    <div class="role"><DESCRIPTION_FROM_PROSE></div>
  </div>
</div>
```

Group by classifying the token name:
- `primary*`, `accent-*`, `brand-*`, `gradient-*` → **Brand & Accent**
- `canvas`, `surface-*`, `inverse-*` → **Surface**
- `ink*`, `body*`, `muted` → **Text**
- `hairline*`, `border-*` → **Borders**
- `success`, `warning`, `error`, `info` → **Semantic**

### 7) Usage proportion bar

The four-segment bar at the end of section 01 visualizes the brand's color density (typically 60–70% canvas / 20–30% support / 5–10% voltage).

If the DESIGN.md doesn't specify proportions, use sensible defaults: 40% canvas / 25% surface-1 / 25% support / 10% voltage. If the brand explicitly publishes different proportions in its manual, match them.

### 8) Typography rows

Section 02 has one `.type-row` per typography token. Generate one row for each role in the brand's `typography:` frontmatter (`display-xl`, `display-lg`, `display-md`, `headline`, `body-lg`, `body`, `caption`, `eyebrow`, `button`, `mono`, etc.).

Per row:
```html
<div class="type-row">
  <div class="type-meta">
    <div class="role">DISPLAY-XL</div>
    <div class="spec"><FAMILY> · <WEIGHT><br><SIZE> / <LINE_HEIGHT> / <LETTER_SPACING></div>
  </div>
  <div class="type-sample t-display-xl"><SAMPLE_TEXT></div>
</div>
```

The `.t-*` CSS classes are predefined for the standard roles. If the brand uses non-standard roles, add inline styles.

Sample text should reflect the brand voice — pull a real tagline from the brand manual when possible, otherwise write a short headline that demonstrates the family at that size.

For `eyebrow`/`caption-uppercase`, render UPPERCASE.
For `mono`, use timecode/path/code-style text appropriate to the brand's domain.

### 9) Button variants

Section 03 has six spec-cards: `button-primary`, `button-primary-states`, `button-secondary`, `button-ghost`, `button-icon`, `text-link`. Keep the structure. Update CTAs and meta lines to reflect the brand's button conventions.

### 10) Cards (section 05)

Three sub-sections: feature cards, pricing, testimonial.
- **Feature cards**: 3-up grid. Generate one per brand pillar/value (varies per brand — some have 3, some 6+; the grid wraps).
- **Pricing**: only include if the brand category warrants it (B2B SaaS, products with tiers). For brands without tiered pricing (luxury, editorial, museums), replace with a different card type or remove.
- **Testimonial**: replace with a brand-appropriate quote. The placeholder "Author Name / Role · Company" must always be replaced — leaving generic placeholder testimonial copy in a final showcase is a quality-bar failure.

### 11) Product UI primitives (section 06) — conditional

The template ships with generic dashboard primitives (KPI tiles, recent-activity rows, settings toggles, inspector). **This entire section is conditional on brand category.**

For specific categories:
- **Software/tools (Linear, Stripe, Vercel)**: keep with brand-relevant primitives (kanban card, dashboard widget, code editor frame, deploy log).
- **Video / audio / creative tools**: timeline track, waveform, render-settings panel, inspector.
- **Consumer/automotive (BMW M, Tesla)**: replace with brand-relevant primitives (carousel, configurator card, model spec table).
- **Editorial/lifestyle (NYT, Medium)**: replace with article cards, byline blocks, related-content lists.
- **Luxury/fashion (Gucci, Prada)**: replace with product card, lookbook frame, atelier story block.
- **No suitable primitive**: skip section 06 entirely. Remove from nav.

### 12) Do's & Don'ts (section 09)

Pull directly from the DESIGN.md "Do's and Don'ts" prose. Each `<li>` is one rule. Bold the leading clause with `<b>`.

### 13) Footer

Update the brand name and copyright year. Optional: replace the version text with something brand-relevant or remove.

## What to keep verbatim

These parts of the template are universal infrastructure — copy unchanged:
- All CSS classes and layout (the `:root` block above; the body styles below).
- Section structure and numbering.
- The `.swatch`, `.spec-card`, `.type-row`, `.feat-card`, `.price-card`, `.testi-card`, `.elev`, `.rad`, `.sp`, `.dodont` patterns.
- Responsive breakpoints and media queries.

## Quality bar for the showcase

The showcase passes if a user opens it and:
1. Recognizes the brand at first glance — no template placeholder copy or colors bleeding through.
2. Sees every color from the DESIGN.md `colors:` section as a swatch.
3. Sees every typography role from the DESIGN.md `typography:` section as a row.
4. Sees the brand's actual Do's and Don'ts (not template placeholders).
5. Has a brand-appropriate section 06 (or no section 06 if not applicable).
6. Renders correctly with a double-click — no fetch errors, no missing fonts.

## Where to save

Save the generated HTML alongside the DESIGN.md as `design-showcase.html`. Same folder. Tell the user where it landed and that they can open it directly with a browser.

## Edge cases

- **Light-canvas brands (Stripe, Apple)**: invert the dark assumptions. Canvas is light; surface lifts go *down* in tone (whites → cream → light gray); ink is near-black. The template uses dark by default but the structure works for light canvases — just substitute tokens.
- **Multi-canvas brands (Notion has both)**: pick the canonical canvas per the DESIGN.md and document the inverse in section 00 alongside the logo variants.
- **Brands without semantic colors**: keep the template's success/warning/error placeholders (or remove the semantic group from section 01) and note in Known Gaps.
- **Brands with > 8 colors**: groups can hold more than 4 swatches; the grid auto-wraps.
- **Brands with very few typography roles**: skip the rows for undefined roles.
