---
name: design-md
description: Author a DESIGN.md file — a single markdown document that captures a brand's visual identity in tokens + prose so AI agents can build pixel-consistent UI from it. Use when the user has a website, brand guide, style guide, mood board, or existing product and wants to distill it into a DESIGN.md (a la getdesign.md / Google Stitch). Triggers - "create a DESIGN.md", "extract design system", "DESIGN.md from this site", "capture this brand", "make design tokens for an AI agent", "Stitch DESIGN.md", "awesome-design-md style".
---

# DESIGN.md Author

Distill a visual identity into a single markdown file that an AI coding agent can read and turn into pixel-consistent UI. The artifact is `DESIGN.md`, the format pioneered by Google Stitch and curated in `awesome-design-md`. It sits beside `AGENTS.md` — `AGENTS.md` says how to build, `DESIGN.md` says how it should look.

## When to use

Invoke this skill when the user wants to:
- Capture a website's visual language into one file (e.g. "make a DESIGN.md for stripe.com")
- Turn a brand guide / style guide / mood board into AI-readable design tokens
- Onboard an AI agent to a project's existing visual identity
- Build a "design.md" the way `awesome-design-md` does it

Do NOT use this skill for:
- Writing a CSS file, Tailwind config, or design-tokens JSON — DESIGN.md is markdown-first, prose + tokens, optimized for LLM reading.
- A mood board or moodboard PDF — that's an input, not an output.
- A figma plugin, code component library, or storybook setup.

## Inputs you need before authoring

Before writing a single line, gather (ask the user concisely if missing):

1. **Identity source** — a URL, a brand book, screenshots, an existing product, or a mood-board description. The skill is only as accurate as its input. If the user has only a vibe ("I want it to feel like Linear meets Notion"), say so and treat the output as inspirational, not extracted.
2. **Surface scope** — marketing site? product UI? mobile app? blog? Default is "marketing surface" the way the awesome-design-md repo treats it.
3. **Light or dark** — many brands ship one or both. Pick the canonical canvas; document the other under Known Gaps if not extracted.
4. **Format choice** — frontmatter (newer, token-first, YAML + prose) vs numbered (older, prose-first, 9 sections). See "Format selection" below. If unspecified, default to **frontmatter**.

If the user gives you a URL with no other constraints, browse it (or ask them to grant access), inspect the live site for hex values, font families, radii, and spacing, then proceed.

## Format selection

Two formats coexist in `awesome-design-md`. Both are valid; pick based on the user's preference and the level of structured tokenization they want.

### Frontmatter format (default — 60% of the corpus)
- YAML frontmatter declares tokens: `colors`, `typography`, `rounded`, `spacing`, `components`.
- Components reference tokens via `{token.refs}` interpolation (e.g. `backgroundColor: "{colors.primary}"`).
- Prose sections below the frontmatter explain the why and how.
- Use when the user wants tokens an LLM can pick up without parsing prose, or when components have many states.
- Spec & full skeleton — see `references/frontmatter-format.md` and `templates/frontmatter.md`.

### Numbered format (older — 40% of the corpus)
- No YAML. Pure markdown with 9 numbered sections, hex values inline.
- Use when the brand has fewer formal tokens, or when prose is more useful than a token graph (heavy editorial / photography-driven brands).
- Spec & full skeleton — see `references/numbered-format.md` and `templates/numbered.md`.

If you're unsure, **default to frontmatter** — it's what newer sites in the corpus use and it gives the agent more to bind to.

## The authoring process

Run these phases in order. Don't skip ahead.

### Phase 1 — Extract raw values

From the source identity, pull:

- **Hex values for**: page canvas, ink/text (heading, body, muted, disabled), brand primary, primary hover/active/focus, surface ladders (1–4 lifts), hairline borders, semantic (success, warning, error), accent decorations (gradients, shadows).
- **Typography**: display family + body family + mono family (with public fallbacks if any are proprietary). For each role: size (px), weight, line-height, letter-spacing.
- **Border radius scale**: smallest (xs, ~4px) → button (md, ~8px) → cards (lg, ~12px) → big tiles (xl, ~16px) → pill (9999px).
- **Spacing scale**: usually a 4px or 8px base, then scale tokens xxs/xs/sm/md/lg/xl/xxl + a section-padding token (typically 64–96px).
- **Components**: buttons (primary, secondary, ghost, inverse, disabled), cards (feature, pricing, testimonial, product-mockup), inputs, navigation, footer, badges/pills, tabs.
- **Shadow / elevation system**: how depth is conveyed (real shadow? surface lift? hairline border? color-block?).
- **Photography & illustration treatment**: dominant or absent? full-bleed? framed in cards? line-art? product UI?

Record every value next to its source observation ("on /pricing, the featured tier card uses..."). If a value cannot be observed, mark it as a Known Gap rather than guessing.

### Phase 2 — Name tokens semantically

Tokens use **role names**, not literal names. The same hex can wear different role names in different brands. Examples:

- `colors.canvas` not `colors.white` — canvas is the role; `#ffffff` is the value.
- `colors.ink` not `colors.gray-900` — ink is the role.
- `colors.primary` for the single signature accent (the one chromatic color a brand defends).
- `colors.surface-1` … `colors.surface-4` for a step-ladder of card backgrounds (use only as many steps as the brand actually uses).
- `colors.hairline` and `colors.hairline-strong` for 1px divider tones.
- `colors.on-primary`, `colors.on-dark` — text colors guaranteed legible on a given surface.
- Semantic: `colors.success`, `colors.warning`, `colors.error`, `colors.info`.

Typography token names follow `display-xl/lg/md/sm`, `headline`, `title-lg/md/sm`, `subhead`, `body-lg/md/sm`, `caption`, `eyebrow`, `button`, `nav-link`, `code`/`mono`. Drop tokens the brand doesn't use; don't pad.

Spacing: `xxs/xs/sm/md/lg/xl/xxl/section`. Border radius: `xs/sm/md/lg/xl/xxl/pill/full`.

### Phase 3 — Pick the canonical canvas + brand voltage

Every DESIGN.md needs to answer two questions in its first paragraph:

1. **What is the canvas?** — the page-level background that anchors the entire system. (Linear: `#010102`. Stripe: `#ffffff`. Claude: cream `#faf9f5`. Vercel: pure white.)
2. **Where is the brand voltage?** — the one chromatic accent, where it goes, and how scarce it is. (Linear: lavender on brand mark + primary CTA + focus only. Stripe: purple on CTA + links. Claude: coral on CTA + full-bleed callout cards.)

If you can't answer both in one sentence each, you haven't extracted enough yet — go back to Phase 1.

### Phase 4 — Write the prose

This is where the file earns its keep. Tokens alone are not enough; an LLM needs the **opinionated voice** that explains how the brand differs from its category. See `references/writing-voice.md` for the full guide. Shortest version:

- **Be specific, not generic.** "Warm coral with slight muted hue" not "orange-ish". "Lavender-blue with negative tracking" not "purple".
- **Compare to peers.** "Where most AI brands use cool blue and slate, Claude uses warm cream and coral." This signals what NOT to default to.
- **Document scarcity rules.** If an accent is used only on the brand mark + primary CTA + focus ring, say exactly that. Otherwise the agent will paint everything that color.
- **Include anti-patterns.** A `Don't` list is half the document's value. "Don't use lavender as a section background. Don't pill-round CTAs. Don't introduce a second chromatic accent."
- **Reference tokens, not raw hex.** In the frontmatter format, write `{colors.primary}` not `#5e6ad2` in the prose. The frontmatter is the source of truth; prose mirrors it.
- **Document what's NOT visible.** Add a Known Gaps section. Light mode missing? Form errors not extracted? Custom proprietary font? Say so.
- **Provide font substitutes.** If the brand uses a proprietary face, name an open-source equivalent (Inter, Geist Sans, JetBrains Mono, EB Garamond, etc.).

### Phase 5 — Assemble & lint

Write the file in the chosen format using the templates. Then sanity-check:

- Does every prose mention of a hex have a matching token in YAML? (frontmatter format)
- Does every component reference real tokens?
- Are state variants (`-hover`, `-active`, `-focused`, `-disabled`, `-pressed`) present where the brand uses them?
- Is the type hierarchy complete from `display-xl` down to `caption`?
- Is the responsive section concrete (named breakpoints + what changes), not "responsive design considered"?
- Is there an `Iteration Guide` (frontmatter) or `Agent Prompt Guide` (numbered) at the end with copy-pasteable agent prompts?
- Do you have at least one `Don't`?

Place the file at the project root.

### Phase 6 — Generate the showcase HTML

Every DESIGN.md ships with a parallel `design-showcase.html` — a single-file, double-clickable visual rendering of the brand's tokens. The user opens it directly with a browser to *see* the system without running a server, parsing markdown, or installing tooling.

**Always do this immediately after Phase 5.** The showcase is part of the deliverable, not an optional extra.

1. Read `templates/showcase.html` — a complete worked example (Sequora Post Production) demonstrating every section, pattern, and CSS class. The template renders end-to-end as Sequora; your job is to adapt every brand-specific spot to the new brand.
2. Read `references/showcase-format.md` — the substitution spec. It documents which `:root` variables map to which frontmatter tokens, which sections are universal vs conditional (e.g. section 06 product UI is only for software/tools brands), and how to handle edge cases (light-canvas brands, brands with no logo, brands with > 8 colors).
3. Adapt the template — **not by replacing `{{placeholders}}` (there are none) but by rewriting Sequora-specific values for the new brand**:
   - `:root` CSS variables → 1:1 mapping with the brand's frontmatter `colors:`, `rounded:`, `spacing:` tokens
   - Google Fonts URL → rebuilt for the brand's display + body + mono families (with weights from the typography section)
   - Logo SVG → inline SVG of the brand's mark (or wordmark-only if no logo provided)
   - Hero copy, section descriptions, card content, testimonials → all rewritten for the brand
   - Color swatches → one per token in `colors:`, auto-grouped (Brand voltage / Surface / Text / Borders+Semantic)
   - Typography rows → one per role in `typography:`
   - Section 06 (product UI primitives) → adapt to brand category or remove entirely
   - Do's & Don'ts → pulled directly from the DESIGN.md prose
4. Save as `design-showcase.html` in the same folder as the DESIGN.md.

The generated HTML must:
- Render correctly when opened with a double-click — no `fetch()`, no local server required, no missing fonts.
- Show every color and typography role from the DESIGN.md.
- Be unmistakably the new brand at a glance — zero Sequora content bleeding through.

Tell the user both files landed (`DESIGN.md` + `design-showcase.html`) and how to use each: DESIGN.md for AI agents to build UI, the HTML to visualize the system. Mention they can also drag the `DESIGN.md` onto a generic viewer (`design-md-viewer.html` if available, or one served from the user's tooling) — but the brand-specific `design-showcase.html` is the canonical visual artifact.

## Voice principles (the non-negotiables)

These show up in every well-written DESIGN.md in the corpus. If a draft is missing them, it reads as generic AI output and the agent will produce generic AI UI.

1. **One canvas, one voltage.** State both in the first paragraph.
2. **Type hierarchy is a complete table**, not bullet points. Size + weight + line-height + letter-spacing per row.
3. **Scarcity rules for accents** — list every place the primary appears, and only those places.
4. **Surface ladder is explicit** — if the brand has 1, 2, 3, or 4 surface lifts, name each and say what lives on each.
5. **Cards are named** — `feature-card`, `pricing-card`, `testimonial-card`, `product-mockup-card-dark`, `cta-banner`. Each gets its own component entry.
6. **Photography & illustration treatment is documented** — even if the answer is "no decorative imagery". Tesla's restraint is as important to capture as Pinterest's masonry.
7. **Known Gaps closes the file** — light mode, animations, form errors, proprietary fonts, sub-product surfaces.

## Quality bar

A finished DESIGN.md should let an agent that has never seen the brand:
- Pick the right canvas color on the first try.
- Pick the right primary CTA color on the first try.
- Use the right font weight at display sizes (e.g. Stripe is 300, not 700).
- Apply the correct border radius (Linear is 8px; Stripe is 4–8px; Notion uses pills).
- Avoid the brand's anti-patterns (no second accent, no pill CTAs where forbidden, no neutral gray shadows where the brand uses tinted shadows).

If you can't simulate "build a hero in this brand's voice" from your draft alone (without the source), the draft is incomplete.

## What to look at when stuck

The corpus at `D:\Antigravity\design-md\design-md\` (when present) is the reference. Particularly strong examples to mimic:

- **Frontmatter, dark, restrained accent**: `linear.app/DESIGN.md`
- **Frontmatter, warm editorial canvas**: `claude/DESIGN.md`
- **Frontmatter, photography-first**: `apple/DESIGN.md`, `nike/DESIGN.md`
- **Numbered, fintech precision**: `stripe/DESIGN.md`
- **Numbered, monochrome engineering**: `vercel/DESIGN.md`
- **Numbered, radical subtraction**: `tesla/DESIGN.md`

Read one in your chosen format end-to-end before writing — the voice is contagious in the right way.

## File map

- `references/frontmatter-format.md` — full spec for the YAML+prose format, section-by-section.
- `references/numbered-format.md` — full spec for the 9-section pure-prose format.
- `references/writing-voice.md` — how to write the prose so it actually steers an agent.
- `references/showcase-format.md` — substitution spec for the showcase HTML template (Phase 6).
- `templates/frontmatter.md` — fillable skeleton for the frontmatter format.
- `templates/numbered.md` — fillable skeleton for the numbered format.
- `templates/showcase.html` — complete worked-example showcase HTML (Sequora Post Production); copied and adapted in Phase 6.

Read the format spec for whichever format you chose, fill the matching template, then in Phase 6 read `references/showcase-format.md` and adapt `templates/showcase.html` for the same brand.
