---
version: alpha
name: <Brand Name>
description: "<One paragraph (3–6 sentences). Open with: '<Brand>'s <surface> is <category descriptor> — a system that <distinguishing trait>.' Then: name the canvas (role + hex), name the brand voltage (role + hex), name the display family + body family + mono family, and end with the ONE thing that makes this brand visually unmistakable. This paragraph stands alone if everything else is truncated.>"

colors:
  # Brand
  primary: "#______"
  on-primary: "#______"
  # primary-hover: "#______"
  # primary-active: "#______"
  # primary-focus: "#______"
  # primary-disabled: "#______"

  # Text
  ink: "#______"
  # body: "#______"
  # body-strong: "#______"
  # ink-muted: "#______"
  # ink-subtle: "#______"
  # ink-tertiary: "#______"

  # Surface (page + cards). Add only the rungs the brand uses.
  canvas: "#______"
  # surface-soft: "#______"
  # surface-1: "#______"
  # surface-2: "#______"
  # surface-3: "#______"
  # surface-4: "#______"
  # surface-card: "#______"
  # surface-dark: "#______"
  # surface-dark-elevated: "#______"
  # inverse-canvas: "#______"
  # inverse-ink: "#______"

  # Borders / hairlines
  # hairline: "#______"
  # hairline-strong: "#______"
  # hairline-soft: "#______"

  # Semantic — include only what is actually visible
  # success: "#______"
  # warning: "#______"
  # error: "#______"
  # info: "#______"
  # semantic-overlay: "#______"

  # Accents — sparing. Examples: accent-teal, accent-amber, brand-navy, card-tint-peach
  # accent-<role>: "#______"

typography:
  display-xl:
    fontFamily: "<Display Family, fallback>"
    fontSize: <px>
    fontWeight: <int>
    lineHeight: <number>
    letterSpacing: <px>
  display-lg:
    fontFamily: "<Display Family, fallback>"
    fontSize: <px>
    fontWeight: <int>
    lineHeight: <number>
    letterSpacing: <px>
  display-md:
    fontFamily: "<Display Family, fallback>"
    fontSize: <px>
    fontWeight: <int>
    lineHeight: <number>
    letterSpacing: <px>
  # display-sm: ...
  # headline: ...
  # title-lg: ...
  title-md:
    fontFamily: "<Body Family, fallback>"
    fontSize: <px>
    fontWeight: <int>
    lineHeight: <number>
    letterSpacing: <px>
  # title-sm: ...
  body-lg:
    fontFamily: "<Body Family, fallback>"
    fontSize: 18px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  body:
    fontFamily: "<Body Family, fallback>"
    fontSize: 16px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  body-sm:
    fontFamily: "<Body Family, fallback>"
    fontSize: 14px
    fontWeight: 400
    lineHeight: 1.50
    letterSpacing: 0
  caption:
    fontFamily: "<Body Family, fallback>"
    fontSize: 12px
    fontWeight: 400
    lineHeight: 1.40
    letterSpacing: 0
  button:
    fontFamily: "<Body Family, fallback>"
    fontSize: 14px
    fontWeight: 500
    lineHeight: 1.20
    letterSpacing: 0
  # eyebrow: ...
  # nav-link: ...
  # mono / code:
  #   fontFamily: "<Mono Family, fallback>"
  #   fontSize: 13px
  #   fontWeight: 400
  #   lineHeight: 1.50
  #   letterSpacing: 0

rounded:
  xs: 4px
  sm: 6px
  md: 8px
  lg: 12px
  xl: 16px
  # xxl: 24px
  pill: 9999px
  full: 9999px

spacing:
  xxs: 4px
  xs: 8px
  sm: 12px
  md: 16px
  lg: 24px
  xl: 32px
  xxl: 48px
  section: 96px

components:
  button-primary:
    backgroundColor: "{colors.primary}"
    textColor: "{colors.on-primary}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 8px 14px
    height: 40px
  # button-primary-hover:
  #   backgroundColor: "{colors.primary-hover}"
  #   textColor: "{colors.on-primary}"
  #   typography: "{typography.button}"
  #   rounded: "{rounded.md}"
  # button-primary-pressed:
  #   backgroundColor: "{colors.primary-active}"
  #   textColor: "{colors.on-primary}"
  #   typography: "{typography.button}"
  #   rounded: "{rounded.md}"
  button-secondary:
    backgroundColor: "{colors.surface-1}"
    textColor: "{colors.ink}"
    typography: "{typography.button}"
    rounded: "{rounded.md}"
    padding: 8px 14px
  # button-tertiary: ...
  # button-inverse: ...
  text-input:
    backgroundColor: "{colors.surface-1}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.md}"
    padding: 8px 12px
    height: 40px
  # text-input-focused: ...
  feature-card:
    backgroundColor: "{colors.surface-1}"
    textColor: "{colors.ink}"
    typography: "{typography.body}"
    rounded: "{rounded.lg}"
    padding: 24px
  # pricing-card: ...
  # pricing-card-featured: ...
  # testimonial-card: ...
  # product-screenshot-card: ...
  # cta-banner: ...
  top-nav:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink}"
    typography: "{typography.body-sm}"
    height: 56px
  footer:
    backgroundColor: "{colors.canvas}"
    textColor: "{colors.ink-subtle}"
    typography: "{typography.caption}"
    padding: 64px 32px
---

## Overview

<Re-state canvas + voltage from the description, with depth. Cover: how surfaces alternate, what the section rhythm is, what dominates the page (product UI / photography / code mockups / illustrations), what the typographic voice is. 2–4 paragraphs.>

**Key Characteristics:**
- <One-line agent-quotable trait — name canvas + a hex>
- <One-line trait about the brand voltage and where it appears>
- <One-line trait about the typographic voice>
- <One-line trait about depth / shadow / surface strategy>
- <One-line trait about photography / illustration treatment>
- <One-line trait about an unusual or signature detail>
- <One-line negative trait — what this brand is NOT doing>

## Colors

> Source pages: <urls or sections inspected>

### Brand & Accent
- **<Display Name>** (`{colors.primary}` — #______): The signature accent — name where it goes.
- **<Display Name>** (`{colors.primary-hover}` — #______): Hover state of the primary.
- <... only the variants the brand actually defines ...>

### Surface
- **Canvas** (`{colors.canvas}` — #______): The default page floor — characterize it.
- **Surface 1** (`{colors.surface-1}` — #______): One step above canvas — what lives here.
- <... continue for each surface rung ...>
- **Hairline** (`{colors.hairline}` — #______): 1px borders on cards and dividers.

### Text
- **Ink** (`{colors.ink}` — #______): Headlines and primary text.
- **<Role>** (`{colors.<token>}` — #______): <where it appears>.

### Semantic
- **<Color>** (`{colors.success}` — #______): <use>.

## Typography

### Font Family

- **<Display Family>** — <description>; fallback `<stack>`. Carries display-xl through <smallest display role>.
- **<Body Family>** — <description>; fallback `<stack>`. Carries body sizes, button labels, captions.
- **<Mono Family>** — <description>; fallback `<stack>`. Used for code.

<One paragraph on how the families relate — is the family change visible or silent? Does mono only appear in code contexts?>

### Hierarchy

| Token | Size | Weight | Line Height | Letter Spacing | Use |
|---|---|---|---|---|---|
| `{typography.display-xl}` | __px | __ | __ | __px | <Largest hero headline use> |
| `{typography.display-lg}` | __px | __ | __ | __px | <use> |
| `{typography.display-md}` | __px | __ | __ | __px | <use> |
| `{typography.title-md}` | __px | __ | __ | __px | <use> |
| `{typography.body-lg}` | __px | __ | __ | __px | <use> |
| `{typography.body}` | __px | __ | __ | __px | Default body |
| `{typography.body-sm}` | __px | __ | __ | __px | <use> |
| `{typography.caption}` | __px | __ | __ | __px | <use> |
| `{typography.button}` | __px | __ | __ | __px | All button labels |

### Principles

- <Typographic non-negotiable — e.g. "aggressive negative tracking on display">
- <Typographic non-negotiable — e.g. "single voice from display to body">
- <Typographic non-negotiable — e.g. "eyebrow uses positive tracking">
- <Typographic non-negotiable — e.g. "mono only in code contexts">

### Note on Font Substitutes

<If the brand uses proprietary or paid fonts, name open-source substitutes. e.g. "Inter at weight 500 / 600 / 700 is the closest free substitute. Geist Sans is also viable. For mono, JetBrains Mono or Geist Mono.">

## Layout

### Spacing System

- **Base unit:** 4px (or 8px).
- **Tokens:** `{spacing.xxs}` 4px · `{spacing.xs}` 8px · `{spacing.sm}` 12px · `{spacing.md}` 16px · `{spacing.lg}` 24px · `{spacing.xl}` 32px · `{spacing.xxl}` 48px · `{spacing.section}` 96px.
- **Section padding:** `{spacing.section}` (96px) — <characterize the rhythm>.
- **Card interior padding:** `{spacing.lg}` 24px on feature cards; `{spacing.xl}` 32px on testimonial cards; `{spacing.xxl}` 48px on CTA banners.

### Grid & Container

- Max content width: ~__px.
- Card grids: __-up at desktop, __-up at tablet, __-up at mobile.
- <Pricing / hero / other grid notes>.

### Whitespace Philosophy

<One paragraph on the brand's whitespace stance: generous, measured, replaced by surface lift, etc.>

## Elevation & Depth

| Level | Treatment | Use |
|---|---|---|
| 0 (flat) | No shadow, no border | Default for body type, hero text, footer |
| 1 (<lift name>) | <treatment> | <Default cards, panels> |
| 2 (<lift name>) | <treatment> | <Featured cards, hovered cards> |
| 3 (<lift name>) | <treatment> | <use> |
| 4 (focus ring) | <treatment> | Focused input, focused button |

<One paragraph on the brand's depth philosophy.>

### Decorative Depth

- <Anything else carrying depth: gradients, scrim, edge highlights, product UI screenshots>
- <Or explicitly: "no atmospheric gradients, no spotlight cards" if the brand resists decoration.>

## Shapes

### Border Radius Scale

| Token | Value | Use |
|---|---|---|
| `{rounded.xs}` | 4px | Small chips, status badges |
| `{rounded.sm}` | 6px | Inline tags |
| `{rounded.md}` | 8px | All buttons, form inputs |
| `{rounded.lg}` | 12px | Pricing cards, feature cards |
| `{rounded.xl}` | 16px | <use> |
| `{rounded.pill}` | 9999px | Pricing tab toggles, status pills |
| `{rounded.full}` | 9999px | Avatar circles |

### Photography & Illustration Geometry

<How are images framed? Edge-to-edge? In `{rounded.xl}` cards? Avatars at `{rounded.full}`? Or: "no decorative photography — the brand uses line-art illustrations / product UI screenshots / no imagery at all">

## Components

### Top Navigation

**`top-nav`** — <one-sentence description>.
- Background `{colors.canvas}`, text `{colors.ink}`, type `{typography.body-sm}`, height 56px.

### Buttons

**`button-primary`** — <description>.
- Background `{colors.primary}`, text `{colors.on-primary}`, type `{typography.button}`, padding 8px 14px, rounded `{rounded.md}`.

**`button-secondary`** — <description>.
- Background `{colors.surface-1}`, text `{colors.ink}`, type `{typography.button}`, padding 8px 14px, rounded `{rounded.md}`.

### Cards & Containers

**`feature-card`** — <description>.
- Background `{colors.surface-1}`, text `{colors.ink}`, type `{typography.body}`, rounded `{rounded.lg}`, padding 24px.

<Add other cards: pricing-card, pricing-card-featured, testimonial-card, product-screenshot-card, etc.>

### Inputs & Forms

**`text-input`** + **`text-input-focused`** — <description>.
- Background `{colors.surface-1}`, text `{colors.ink}`, type `{typography.body}`, rounded `{rounded.md}`, padding 8px 12px.

### Tags / Badges

**`status-badge`** — <description>.

### CTA / Footer

**`cta-banner`** — <description>.

**`footer`** — <description>.
- Background `{colors.canvas}`, text `{colors.ink-subtle}`, type `{typography.caption}`, padding 64px 32px.

## Do's and Don'ts

### Do

- <Concrete rule about the canvas>
- <Concrete rule about the primary accent and where it goes>
- <Concrete rule about the surface ladder>
- <Concrete rule about display weight and tracking>
- <Concrete rule about photography / illustration treatment>
- <Concrete rule about CTA shape and radius>
- <Concrete rule about section rhythm>

### Don't

- <Concrete anti-pattern — names a specific value or pattern>
- <Concrete anti-pattern — opposes a generic AI default>
- <Concrete anti-pattern — names a wrong second accent>
- <Concrete anti-pattern — names a wrong shape (e.g. "Don't pill-round CTAs")>
- <Concrete anti-pattern — about depth / shadow>
- <Concrete anti-pattern — about light/dark mode if applicable>
- <Concrete anti-pattern — about typographic weight>

## Responsive Behavior

### Breakpoints

| Name | Width | Key Changes |
|---|---|---|
| Desktop-XL | 1440px | Default desktop layout |
| Desktop | 1280px | Card grid 3-up maintained |
| Tablet | 1024px | Card grid 3-up → 2-up |
| Mobile-Lg | 768px | <change>; nav hamburger |
| Mobile | 480px | Single-column; display-xl scales __px → __px |

### Touch Targets

- CTAs hold ≥40px tap height across viewports.
- <Other components and their tap heights>.

### Collapsing Strategy

- **Top nav**: links collapse to hamburger below 768px.
- **Card grids**: 3-up → 2-up at 1024px → 1-up below 768px.
- **Display type**: `{typography.display-xl}` __px scales toward `{typography.display-md}` __px on mobile.

### Image Behavior

- <How product screenshots / photography / illustrations behave responsively>.

## Iteration Guide

1. Focus on ONE component at a time and reference it by its `components:` token name.
2. When introducing a section, decide first which surface lift it lives on.
3. Default body to `{typography.body}` at weight 400.
4. Variants of an existing component (`-active`, `-disabled`, `-focused`) live as separate entries in `components:`.
5. Use `{token.refs}` everywhere — never inline hex.
6. Treat `{colors.primary}` as scarce: <list the only places it appears>.
7. <Brand-specific iteration rule>.
8. <Brand-specific iteration rule>.

## Known Gaps

- <What was not extracted from the source>
- <What is proprietary and substituted (e.g. proprietary fonts with named substitutes)>
- <Light mode (or dark mode) not shipped>
- <Form validation states beyond focus>
- <Animation / transition timings>
- <Sub-product surfaces vs marketing surface>
