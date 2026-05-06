# Numbered Format Spec

The older, prose-first DESIGN.md format. Used by ~40% of `awesome-design-md` (Stripe, Vercel, Tesla, Spotify, Shopify, Lamborghini, Mastercard, Sanity, Sentry, Supabase, Superhuman, Uber, Vodafone, Warp, Webflow, Wired, Wise, x.ai, Zapier, RunwayML, Lovable, Kraken, SpaceX, theverge, together.ai, voltagent, Starbucks).

No YAML frontmatter. Pure markdown. Hex values appear inline in backticks. Nine numbered sections, in fixed order.

## File shape

```
# Design System Inspired by <Brand>

## 1. Visual Theme & Atmosphere
...

## 2. Color Palette & Roles
...

## 3. Typography Rules
...

## 4. Component Stylings
...

## 5. Layout Principles
...

## 6. Depth & Elevation
...

## 7. Do's and Don'ts
...

## 8. Responsive Behavior
...

## 9. Agent Prompt Guide
...
```

## Section-by-section spec

### `# Design System Inspired by <Brand>`
H1 heading. Use the brand's proper name as it appears in marketing.

### `## 1. Visual Theme & Atmosphere`

3–5 paragraphs (~300–600 words) plus a `**Key Characteristics:**` bullet list of 6–9 items at the end.

The first paragraph must answer:
- What is the canvas color (hex inline)?
- What is the brand's primary chromatic anchor (hex inline)?
- What is the typographic voice (display family + body family)?
- What is this brand's ONE distinguishing visual idea — the thing no other brand in its category does?

Subsequent paragraphs unpack:
- The fonts in detail — weights used, OpenType features, letter-spacing strategy, why this typographic choice signals this brand.
- The depth / shadow / elevation strategy — what makes it brand-specific (Stripe's blue-tinted shadows, Vercel's shadow-as-border).
- Section rhythm and pacing — what alternates, what dominates.

The `**Key Characteristics:**` bullet list closes the section. Each bullet is one line, agent-quotable. Examples:
- "Geist Sans with extreme negative letter-spacing (-2.4px to -2.88px at display) — text as compressed infrastructure"
- "Shadow-as-border technique: `box-shadow 0px 0px 0px 1px` replaces traditional borders throughout"
- "Single accent color — Electric Blue (`#3E6AE1`) — used exclusively for primary CTA buttons"

### `## 2. Color Palette & Roles`

Group with H3 subheadings. Each color is bulleted as:
```
- **Display Name** (`#hex`): What it's used for, ideally citing a CSS variable or specific page.
```

Example:
```
- **Stripe Purple** (`#533afd`): Primary brand color, CTA backgrounds, link text, interactive highlights.
- **Deep Navy** (`#061b31`): `--hds-color-heading-solid`. Primary heading color. Not black, not gray — a very dark blue that adds warmth and depth to text.
```

Standard subgrouping:
- `### Primary` — page background + primary CTA + heading color
- `### Brand & Dark` (or `### Secondary & Accent`) — branded sub-tones for dark sections, footer
- `### Accent Colors` — decorative accents (gradient endpoints, illustration colors)
- `### Interactive` — hover/active/focus variants of primary
- `### Neutral Scale` — heading / label / body / muted gradient
- `### Surface & Borders` — borders, dividers, surface tints
- `### Shadow Colors` — if the shadow system uses tinted RGBA values, list them

Only include subgroups the brand uses. Don't pad with empty sections.

### `## 3. Typography Rules`

Three subsections:

**`### Font Family`**
Bullet list. Format:
```
- **Primary**: <name>, with fallback: <stack>
- **Monospace**: <name>, with fallback: <stack>
- **OpenType Features**: `"<feature>"` enabled globally on <where>; `"<feature>"` for <use>.
```

Stripe sample:
```
- **Primary**: `sohne-var`, with fallback: `SF Pro Display`
- **Monospace**: `SourceCodePro`, with fallback: `SFMono-Regular`
- **OpenType Features**: `"ss01"` enabled globally on all sohne-var text; `"tnum"` for tabular numbers on financial data and captions.
```

**`### Hierarchy`**
A markdown table with columns:
| Role | Font | Size | Weight | Line Height | Letter Spacing | (Features) | (Notes) |

The `Features` column captures OpenType activations (`ss01`, `tnum`, `liga`, uppercase, etc.). The `Notes` column carries one-line context ("Maximum size, whisper-weight authority").

Roles to include (skip what brand doesn't use):
- Display Hero (largest)
- Display Large
- Section Heading
- Sub-heading Large
- Sub-heading
- Body Large
- Body
- Button
- Button Small
- Link
- Caption / Caption Small / Caption Tabular
- Micro / Nano (very small labels — financial brands often have these)
- Code Body / Code Bold / Code Label / Code Micro

**`### Principles`**
Bullet list of typographic rules. Examples to consider:
- "Light weight as signature": brand-specific weight choice
- "ss01 everywhere" or other globally-enabled OpenType
- "Two-weight simplicity": the actual weight count in use
- "Progressive tracking": how letter-spacing changes with size
- "ALL CAPS only on X" or "Mixed case throughout"

### `## 4. Component Stylings`

Subgroup by component family:
- `### Buttons`
- `### Cards & Containers`
- `### Badges / Tags / Pills`
- `### Inputs & Forms`
- `### Navigation`
- `### Decorative Elements`

Each component is a labeled block. Format:
```
**Component Name**
- Background: `<hex or token>`
- Text: `<hex>`
- Padding: <values>
- Radius: <px>
- Border: `<spec>`
- Font: <typography line>
- Hover: <state spec>
- Use: <where it appears>
```

Stripe button sample:
```
**Primary Purple**
- Background: `#533afd`
- Text: `#ffffff`
- Padding: 8px 16px
- Radius: 4px
- Font: 16px sohne-var weight 400, `"ss01"`
- Hover: `#4434d4` background
- Use: Primary CTA ("Start now", "Contact sales")
```

Multiple variants stack as separate labeled blocks (`Primary Purple`, `Ghost / Outlined`, `Transparent Info`, `Neutral Ghost`).

For cards, the spec block can be a single bulleted list rather than per-card blocks if there's just one card style:
```
### Cards & Containers
- Background: `#ffffff`
- Border: `1px solid #e5edf5`
- Radius: 4px (tight), 5px (standard), 6px (comfortable), 8px (featured)
- Shadow (standard): `<shadow string>`
- Hover: shadow intensifies
```

### `## 5. Layout Principles`

Subsections:
- `### Spacing System` — base unit + scale values
- `### Grid & Container` — max width, hero treatment, feature grid columns, section width strategy
- `### Whitespace Philosophy` — one paragraph on the brand's whitespace stance
- `### Border Radius Scale` — list of radii from micro to large

Spacing system example:
```
- Base unit: 8px
- Scale: 1px, 2px, 4px, 6px, 8px, 10px, 11px, 12px, 14px, 16px, 18px, 20px
- Notable: The scale is dense at the small end (every 2px from 4-12), reflecting Stripe's precision-oriented UI for financial data
```

Border radius scale example:
```
- Micro (1px): Fine-grained elements, subtle rounding
- Standard (4px): Buttons, inputs, badges, cards — the workhorse
- Comfortable (5px): Standard card containers
- Relaxed (6px): Navigation, larger interactive elements
- Large (8px): Featured cards, hero elements
- Compound: `0px 0px 6px 6px` for bottom-rounded containers (tab panels, dropdown footers)
```

### `## 6. Depth & Elevation`

A markdown table:
| Level | Treatment | Use |
|---|---|---|
| Flat (Level 0) | No shadow | Page background |
| Ambient (Level 1) | `<shadow string>` | Subtle card lift |
| Standard (Level 2) | `<shadow string>` | Standard cards |
| Elevated (Level 3) | `<shadow string>` | Featured cards, popovers |
| Deep (Level 4) | `<shadow string>` | Modals, floating panels |
| Ring | `2px solid <hex>` | Keyboard focus ring |

After the table, a `**Shadow Philosophy**:` paragraph (one to two paragraphs) on what makes the brand's elevation specific. Stripe is "chromatic depth — blue-tinted shadows that echo the navy palette." Vercel is "shadow-as-border, replacing CSS borders with `box-shadow 0 0 0 1px`." Tesla is "no elevation at all — radical subtraction."

A `### Decorative Depth` subsection describes anything else carrying depth (gradients, scrims, glass effects, dark sections).

### `## 7. Do's and Don'ts`

Two subsections, `### Do` and `### Don't`. Each is a bulleted list of 6–9 items.

Each Don't should be specific and oppose a generic-AI default. Examples that work:
- "Don't use weight 600-700 for sohne-var headlines — weight 300 is the brand voice"
- "Don't use neutral gray shadows — always tint with blue (`rgba(50,50,93,...)`)"
- "Don't skip `\"ss01\"` on any sohne-var text"
- "Don't use large border-radius (12px+, pill shapes) on cards or buttons — Stripe is conservative"

### `## 8. Responsive Behavior`

Subsections:

**`### Breakpoints`** — table:
| Name | Width | Key Changes |
|---|---|---|
| Mobile | <640px | Single column, reduced heading sizes |
| Tablet | 640–1024px | 2-column grids, moderate padding |
| Desktop | 1024–1280px | Full layout, 3-column feature grids |
| Large Desktop | >1280px | Centered content with generous margins |

**`### Touch Targets`** — bullet list of minimum tap heights for buttons, pills, nav, mobile toggle.

**`### Collapsing Strategy`** — bullet list of how the layout reduces from desktop → tablet → mobile (column counts, navigation, hero scaling, data tables).

**`### Image Behavior`** — how photography, code blocks, dashboards behave responsively.

### `## 9. Agent Prompt Guide`

This section is unique to the numbered format. Three subsections:

**`### Quick Color Reference`**
Bulleted recap of the most-used colors:
```
- Primary CTA: <Brand Color> (`#hex`)
- CTA Hover: <Color> (`#hex`)
- Background: <Color> (`#hex`)
- Heading text: <Color> (`#hex`)
- Body text: <Color> (`#hex`)
- Border: <Color> (`#hex`)
- Link: <Color> (`#hex`)
- Dark section: <Color> (`#hex`)
- Success: <Color> (`#hex`)
- Accent decorative: <Color> (`#hex`)
```

**`### Example Component Prompts`**
3–6 quoted, ready-to-paste agent prompts that describe specific components in concrete spec form. Each prompt is a single string that an agent can lift verbatim. Examples (Stripe):

```
- "Create a hero section on white background. Headline at 48px sohne-var weight 300, line-height 1.15, letter-spacing -0.96px, color #061b31, font-feature-settings 'ss01'. Subtitle at 18px weight 300, line-height 1.40, color #64748d. Purple CTA button (#533afd, 4px radius, 8px 16px padding, white text) and ghost button (transparent, 1px solid #b9b9f9, #533afd text, 4px radius)."

- "Design a card: white background, 1px solid #e5edf5 border, 6px radius. Shadow: rgba(50,50,93,0.25) 0px 30px 45px -30px, rgba(0,0,0,0.1) 0px 18px 36px -18px. Title at 22px sohne-var weight 300, letter-spacing -0.22px, color #061b31, 'ss01'. Body at 16px weight 300, #64748d."

- "Build a success badge: rgba(21,190,83,0.2) background, #108c3d text, 4px radius, 1px 6px padding, 10px sohne-var weight 300, border 1px solid rgba(21,190,83,0.4)."
```

These prompts are the "if your agent can read only one section, this is the section" deliverable.

**`### Iteration Guide`**
Numbered list (5–8 items) of workflow rules for an agent extending the system. Examples:
1. Always enable `font-feature-settings: "ss01"` on sohne-var text — this is the brand's typographic DNA
2. Weight 300 is the default; use 400 only for buttons/links/navigation
3. Shadow formula: `<formula>` where Y1/B1 are larger (far shadow) and Y2/B2 are smaller (near shadow)
4. Heading color is `#061b31` (deep navy), body is `#64748d` (slate), labels are `#273951` (dark slate)

## Reference: real numbered-format files in `awesome-design-md`

When in doubt, mimic the voice and structure of:
- `stripe/DESIGN.md` — fintech precision, multi-layer shadows, weight-300 luxury
- `vercel/DESIGN.md` — engineering minimalism, shadow-as-border, Geist
- `tesla/DESIGN.md` — radical subtraction, photography-first
- `spotify/DESIGN.md` — vibrant green, dark cinematic
- `mastercard/DESIGN.md` — orbital pill shapes, editorial warmth
