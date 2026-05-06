# Design System Inspired by <Brand>

## 1. Visual Theme & Atmosphere

<Open with the category-defining sentence: "<Brand>'s website is <category descriptor> — a system that <distinguishing trait>." Then in the same paragraph: name the canvas (hex inline), the brand primary (hex inline), the typographic voice (display family + body family), and the ONE distinguishing visual idea.>

<Second paragraph: detail the typography. Custom font name, weights actually in use, OpenType features enabled globally, letter-spacing strategy at display sizes, why the typographic choice signals this brand.>

<Third paragraph: detail the depth / shadow / elevation strategy. What's brand-specific about it? Tinted shadows? Shadow-as-border? No shadows at all? Surface lift? Hairline borders?>

<Fourth paragraph (optional): section rhythm and pacing — what alternates, what dominates, where photography / product UI / code mockups carry weight.>

**Key Characteristics:**
- <One-line trait — name a specific value or technique that defines the brand>
- <One-line trait — about the typographic voice>
- <One-line trait — about the shadow / elevation system>
- <One-line trait — about the canvas + primary pairing>
- <One-line trait — about photography or illustration treatment>
- <One-line trait — about an unusual or signature detail>
- <One-line trait — about what the brand does NOT do>

## 2. Color Palette & Roles

### Primary
- **<Brand Color>** (`#______`): Primary brand color, CTA backgrounds, link text, interactive highlights. <Characterize what kind of <color> it is — not generic.>
- **<Heading Color>** (`#______`): Primary heading color. <Why this and not pure black?>
- **Pure White** (`#______`): Page background, card surfaces, button text on dark backgrounds.

### Brand & Dark
- **<Color>** (`#______`): <Use — dark sections, footer backgrounds, immersive brand moments>.
- **<Color>** (`#______`): The darkest neutral — characterize.

### Accent Colors
- **<Color>** (`#______`): <Use — icons, alerts, gradient endpoints>.
- **<Color>** (`#______`): <Use — decorative highlights>.

### Interactive
- **<Color>** (`#______`): Primary link color, active states, selected elements.
- **<Color>** (`#______`): Hover state for primary.
- **<Color>** (`#______`): <Subdued hover, range selector, etc.>.

### Neutral Scale
- **Heading** (`#______`): Primary headings, nav text, strong labels.
- **Label** (`#______`): Form labels, secondary headings.
- **Body** (`#______`): Secondary text, descriptions, captions.
- **Success** (`#______`): Status badges, success indicators.
- **<Color>** (`#______`): Warning / highlight accent.

### Surface & Borders
- **Border Default** (`#______`): Standard border color for cards, dividers, containers.
- **Border <Variant>** (`#______`): <Use>.
- **<Border type>** (`#______`): <Use>.

### Shadow Colors
- **<Shadow Name>** (`rgba(__,__,__,0.__)`): The signature — <characterize what's brand-specific about it>.
- **<Shadow Layer 2>** (`rgba(__,__,__,0.__)`): Secondary shadow layer for depth reinforcement.
- **<Soft / Ambient>** (`rgba(__,__,__,0.__)`): Soft ambient shadow for subtle elevation.

## 3. Typography Rules

### Font Family
- **Primary**: `<font-name>`, with fallback: `<fallback>`
- **Monospace**: `<font-name>`, with fallback: `<fallback>`
- **OpenType Features**: `"<feature>"` enabled <where>; `"<feature>"` for <use>.

### Hierarchy

| Role | Font | Size | Weight | Line Height | Letter Spacing | Features | Notes |
|------|------|------|--------|-------------|----------------|----------|-------|
| Display Hero | <font> | __px | __ | __ | __px | <feature> | Maximum size, <characterization> |
| Display Large | <font> | __px | __ | __ | __px | <feature> | Secondary hero headlines |
| Section Heading | <font> | __px | __ | __ | __px | <feature> | Feature section titles |
| Sub-heading Large | <font> | __px | __ | __ | __px | <feature> | Card headings, sub-sections |
| Sub-heading | <font> | __px | __ | __ | __px | <feature> | Smaller section heads |
| Body Large | <font> | __px | __ | __ | normal | <feature> | Feature descriptions, intro text |
| Body | <font> | __px | __ | __ | normal | <feature> | Standard reading text |
| Button | <font> | __px | __ | __ | normal | <feature> | Primary button text |
| Button Small | <font> | __px | __ | __ | normal | <feature> | Secondary/compact buttons |
| Link | <font> | __px | __ | __ | normal | <feature> | Navigation links |
| Caption | <font> | __px | __ | normal | normal | <feature> | Small labels, metadata |
| Caption Small | <font> | __px | __ | __ | normal | <feature> | Fine print, timestamps |
| Code Body | <mono> | __px | __ | __ | normal | -- | Code blocks, syntax |
| Code Bold | <mono> | __px | __ | __ | normal | -- | Bold code, keywords |

### Principles
- **<Signature trait>**: <e.g. "Light weight as signature: weight 300 at display sizes is the brand's most distinctive typographic choice.">
- **<OpenType discipline>**: <e.g. "ss01 everywhere — modifies specific glyphs to create a more geometric feel.">
- **<Tracking strategy>**: <e.g. "Progressive tracking: letter-spacing tightens proportionally with size.">
- **<Weight discipline>**: <e.g. "Two-weight simplicity — primarily 300 (body and headings) and 400 (UI/buttons).">

## 4. Component Stylings

### Buttons

**<Button Variant Name>**
- Background: `#______`
- Text: `#______`
- Padding: __px __px
- Radius: __px
- Font: __px <font> weight __, `"<feature>"`
- Hover: `#______` background
- Use: <Where this appears>

**<Second Variant>**
- Background: <transparent / hex>
- Text: `#______`
- Padding: __px __px
- Radius: __px
- Border: `1px solid #______`
- Font: __px <font> weight __, `"<feature>"`
- Hover: <state spec>
- Use: <Where>

### Cards & Containers
- Background: `#______`
- Border: `1px solid #______`
- Radius: __px (tight), __px (standard), __px (comfortable), __px (featured)
- Shadow (standard): `<shadow string>`
- Shadow (ambient): `<shadow string>`
- Hover: <state spec>

### Badges / Tags / Pills

**<Badge Variant>**
- Background: `#______`
- Text: `#______`
- Padding: __px __px
- Radius: __px
- Border: `1px solid #______`
- Font: __px weight __

### Inputs & Forms
- Border: `1px solid #______`
- Radius: __px
- Focus: `1px solid #______` or <ring spec>
- Label: `#______`, __px <font>
- Text: `#______`
- Placeholder: `#______`

### Navigation
- <Layout description — sticky? blur? brand position?>
- Brand logotype <position>
- Links: <font> __px weight __, `#______` text with `"<feature>"`
- Radius: __px on nav container
- CTA: <description and color>
- Mobile: <toggle description>

### Decorative Elements
**<Element type>**
- <spec>

**<Gradient or motif>**
- <description>

## 5. Layout Principles

### Spacing System
- Base unit: __px
- Scale: __px, __px, __px, __px, __px, __px, __px, __px, __px, __px, __px, __px
- Notable: <one-line characterization of how the scale is structured>

### Grid & Container
- Max content width: ~__px
- Hero: <description>
- Feature sections: <column count> grids
- <Other layout patterns specific to the brand>
- Code/dashboard previews as <treatment>

### Whitespace Philosophy
- **<Philosophy name>**: <one paragraph on whether whitespace is generous, measured, dense, or replaced by surface contrast>
- <Section rhythm description>

### Border Radius Scale
- Micro (__px): <use>
- Standard (__px): Buttons, inputs, badges, cards — <characterize>
- Comfortable (__px): Standard card containers
- Relaxed (__px): Navigation, larger interactive elements
- Large (__px): Featured cards, hero elements
- Compound: `<spec>` for <use>

## 6. Depth & Elevation

| Level | Treatment | Use |
|-------|-----------|-----|
| Flat (Level 0) | No shadow | Page background, inline text |
| Ambient (Level 1) | `<shadow string>` | Subtle card lift, hover hints |
| Standard (Level 2) | `<shadow string>` | Standard cards, content panels |
| Elevated (Level 3) | `<shadow string>` | Featured cards, dropdowns, popovers |
| Deep (Level 4) | `<shadow string>` | Modals, floating panels |
| Ring (Accessibility) | `<spec>` | Keyboard focus ring |

**Shadow Philosophy**: <One to two paragraphs on what makes the brand's elevation specific. Tinted shadows? Multi-layer? Shadow-as-border? No elevation at all? Why?>

### Decorative Depth
- <Anything else carrying depth — gradient overlays, dark sections, scrim, glass effects>
- <Or explicit absence: "No drop shadows, no gradients, no decorative depth">

## 7. Do's and Don'ts

### Do
- <Use <signature font feature> on every <element> — the <feature> IS the brand>
- <Use weight __ for <element>>
- <Apply <shadow / surface treatment>>
- <Use <heading color> for headings instead of #000000 — <reason>>
- <Keep border-radius between __px and __px>
- <Use <feature> for <specific use>>
- <Layer / pair <treatments> for <effect>>
- <Use <primary color> as the primary interactive/CTA color>

### Don't
- <Don't use weight __ for headlines — weight __ is the brand voice>
- <Don't use large border-radius / pill shapes on <where>>
- <Don't use neutral gray shadows — always <alternative>>
- <Don't skip <signature feature> on any text>
- <Don't use pure black for headings — always <alternative>>
- <Don't use <wrong accent> for interactive elements — <correct color> is primary>
- <Don't apply <wrong tracking direction> at display sizes>
- <Don't use <decorative color> for buttons or links>

## 8. Responsive Behavior

### Breakpoints
| Name | Width | Key Changes |
|------|-------|-------------|
| Mobile | <__px | Single column, reduced heading sizes, stacked cards |
| Tablet | __–__px | <column count> grids, moderate padding |
| Desktop | __–__px | Full layout, <column count> feature grids |
| Large Desktop | >__px | Centered content with generous margins |

### Touch Targets
- Buttons use comfortable padding (__px–__px vertical)
- Navigation links at __px with adequate spacing
- Badges have __px horizontal padding minimum for tap targets
- Mobile nav toggle with __px radius button

### Collapsing Strategy
- Hero: __px display → __px on mobile, weight __ maintained
- Navigation: horizontal links + CTAs → hamburger toggle
- Feature cards: <count>-column → <count>-column → single column stacked
- <Other section-specific responsive behavior>
- Section spacing: __px+ → __px on mobile
- Typography scale compresses: __px → __px → __px hero sizes across breakpoints

### Image Behavior
- Dashboard/product screenshots <responsive treatment>
- Hero <decorative element> simplifies on mobile
- Code blocks maintain `<mono>` treatment, <wrap or scroll behavior>
- Card images maintain consistent __px–__px border-radius

## 9. Agent Prompt Guide

### Quick Color Reference
- Primary CTA: <Brand Color> (`#______`)
- CTA Hover: <Color> (`#______`)
- Background: <Canvas> (`#______`)
- Heading text: <Color> (`#______`)
- Body text: <Color> (`#______`)
- Label text: <Color> (`#______`)
- Border: <Color> (`#______`)
- Link: <Color> (`#______`)
- Dark section: <Color> (`#______`)
- Success: <Color> (`#______`)
- Accent decorative: <Color> (`#______`)

### Example Component Prompts
- "Create a hero section on <canvas> background. Headline at __px <font> weight __, line-height __, letter-spacing __px, color #______, font-feature-settings '<feature>'. Subtitle at __px weight __, line-height __, color #______. <Primary> CTA button (#______, __px radius, __px __px padding, white text) and <secondary> button (transparent, 1px solid #______, #______ text, __px radius)."

- "Design a card: <canvas> background, 1px solid #______ border, __px radius. Shadow: <shadow string>. Title at __px <font> weight __, letter-spacing __px, color #______, '<feature>'. Body at __px weight __, #______."

- "Build a <success / status / badge>: <bg color> background, #______ text, __px radius, __px __px padding, __px <font> weight __, border 1px solid <border color>."

- "Create navigation: <canvas> sticky header with backdrop-filter blur(__px). <font> __px weight __ for links, #______ text, '<feature>'. <Primary> CTA right-aligned (#______ bg, white text, __px radius). Nav container __px radius."

- "Design a dark brand section: #______ background, white text. Headline __px <font> weight __, letter-spacing __px, '<feature>'. Body __px weight __, rgba(255,255,255,__). Cards inside use rgba(255,255,255,__) border with __px radius."

### Iteration Guide
1. Always enable `font-feature-settings: "<feature>"` on <font> text — this is the brand's typographic DNA
2. Weight __ is the default; use __ only for <where>
3. Shadow formula: `<formula>` where <component meanings>
4. Heading color is `#______` (<role>), body is `#______` (<role>), labels are `#______` (<role>)
5. Border-radius stays in the __px–__px range — never use <wrong shape>
6. Use `"<feature>"` for any <where>
7. Dark sections use `#______` — not black, not gray, but <characterization>
8. <Mono font> for code at __px/__ with __ line-height (<characterize>)
