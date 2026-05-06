# Writing Voice — How DESIGN.md Prose Actually Works

Tokens tell an agent what colors and sizes to use. Prose tells the agent **why one brand looks like this and not like every other site**. Without the prose voice, the agent will produce generic AI UI even with perfect tokens.

The `awesome-design-md` corpus has a distinctive voice. It's not casual. It's not academic. It's the voice of a working designer briefing a colleague, with strong opinions, comparative claims, and named anti-patterns.

Read this file before writing the prose sections of any DESIGN.md.

## The seven voice principles

### 1. Specific words beat generic words

Bad → "The brand uses a purple primary color."
Good → "The signature is **Stripe Purple** (`#533afd`) — a saturated blue-violet that anchors the entire system. Not the cold, clinical purple of enterprise software; a rich, saturated violet that reads as confident and premium."

Bad → "Headlines are large."
Good → "Display sizes use weight 300 — an extraordinarily light weight for headlines that creates an ethereal, almost whispered authority. This is the opposite of the 'bold hero headline' convention; Stripe's headlines feel like they don't need to shout."

The prose carries opinion AND a specific contrast that anchors the choice.

### 2. Compare to the category

Brand voice lives in opposition. Always say what the brand is NOT doing that its peers do.

Examples from the corpus:
- "Where most AI brands use cool blue and slate, Claude uses warm cream and coral — deliberately humanist."
- "Where other design systems use neutral gray or black shadows, Stripe's primary shadow color (`rgba(50,50,93,0.25)`) is a deep blue-gray that echoes the brand's navy palette."
- "Linear's marketing canvas is the deepest dark surface in this collection — `#010102`, essentially pure black with a faint blue tint."
- "This is the opposite of the 'bold hero headline' convention."

A comparative claim tells the agent: when in doubt, default the OTHER way.

### 3. Document scarcity rules explicitly

The most common failure mode of brand-naive agents is over-applying the accent color. Combat this by listing every place the accent appears, and ONLY those places.

Linear:
> "Use `{colors.primary}` lavender ONLY for: brand mark, primary CTA, focus ring, link emphasis."

Claude:
> "Reserve `{colors.primary}` (coral) for primary CTAs and full-bleed `{component.callout-card-coral}` moments. Don't paint accent moments coral elsewhere."

Vercel:
> "Workflow accent colors — Ship Red (`#ff5b4f`), Preview Pink (`#de1d8d`), Develop Blue (`#0a72ef`) — appear only on workflow-step labels, never as buttons or links."

When you read this in the source, the rule should appear in BOTH the Overview prose AND the Do's/Don'ts list.

### 4. Don't lists are half the document's value

Most templates focus on what TO do. The DESIGN.md format leans hard on what NOT to do. The Don'ts encode the negative space of the brand.

Strong Don'ts share three properties:
- **Concrete**: name a specific value or pattern, not a vibe.
- **Anti-default**: oppose a generic AI tendency.
- **Reasoned**: imply WHY this is wrong, even briefly.

Examples:
- "Don't use `#000000` true black as the canvas." (Specific — names the wrong hex.)
- "Don't pill-round CTAs." (Specific — names the wrong shape.)
- "Don't use weight 600-700 for sohne-var headlines — weight 300 is the brand voice." (Anti-default + reasoned.)
- "Don't introduce a second chromatic accent (orange, pink, green for marketing)." (Anti-default with examples.)
- "Don't ship a light-mode marketing page." (For dark-only brands.)
- "Don't use neutral gray shadows — always tint." (Anti-default + alternative.)
- "Don't bold serif display weight. Copernicus at 700 reads as bombastic; the system stays at 400." (Reasoned.)

Weak Don'ts to avoid: "Don't make it ugly", "Don't be inconsistent", "Don't ignore accessibility". Generic, unfalsifiable, useless.

### 5. Use semantic role names, not literal names

Never write "the white color" — write "the canvas", "the page background", "the surface above canvas". Never write "the gray text" — write "the muted body text" or "the tertiary ink". Roles travel; literals don't.

In the frontmatter format the role IS the token name (`{colors.canvas}`, `{colors.ink-muted}`). In the numbered format, write the role next to the literal (`Stripe Purple (#533afd)`, `Deep Navy (#061b31)`, `Slate (#64748d)`).

### 6. Cross-reference, don't restate

In the frontmatter format, prose mentions of design values use the token reference, not the raw value:
- Good → "The default page floor is `{colors.canvas}` (#faf9f5) — tinted cream."
- Bad → "The default page floor is #faf9f5 — tinted cream."

The token reference makes the prose machine-rewritable: change the YAML once, and every prose mention stays correct.

In the numbered format, hex stays inline since there's no YAML source of truth — but always pair it with a role name on first introduction.

### 7. Document what's NOT visible

Every DESIGN.md ends with a Known Gaps section (frontmatter format) or has gap-flags scattered through (numbered format). Honesty here prevents the agent from hallucinating values that weren't on the source.

Common gaps to acknowledge:
- Light mode not extracted (or dark mode, depending on which canvas the source ships).
- Form validation states beyond focus.
- Animation and transition timings.
- Proprietary fonts not publicly distributed (with substitute already named).
- Sub-product surfaces (in-app UI) vs marketing surface.
- Micro-interactions like hover states on tertiary elements.

A clean "we did not extract X" beats a guessed-at value.

## Sentence patterns that work

These patterns appear throughout the corpus and steer the prose toward the right voice:

**The category-defining sentence** (open the description / overview with this):
> "<Brand>'s website is <category descriptor> — a system that <distinguishing trait>."

Examples:
- "Stripe's website is the gold standard of fintech design — a system that manages to feel simultaneously technical and luxurious, precise and warm."
- "Vercel's website is the visual thesis of developer infrastructure made invisible — a design system so restrained it borders on philosophical."
- "Tesla's website is an exercise in radical subtraction — a digital showroom where the product is everything and the interface is almost nothing."

**The token + characterization sentence**:
> "<Brand Color> (`#hex`) — <one-line characterization that distinguishes it from a generic version of the same color>."

Examples:
- "Lavender-blue (#5e6ad2) — a confident, mid-saturation blue that stands alone as the only chromatic color in the entire interface."
- "Vercel Black (#171717) — not pure black; the slight warmth prevents harshness."
- "Stripe Purple (#533afd) — a saturated blue-violet that anchors the entire system. This isn't the cold, clinical purple of enterprise software."

**The scarcity-rule sentence**:
> "<Color> appears <only here, here, and here> — never <where you'd expect it>."

Examples:
- "The accent lavender appears on the brand mark, focus rings, and a few intentional CTAs — never decoratively."
- "The single accent color is Electric Blue, used exclusively for primary CTA buttons. Tesla deliberately avoids color variety."

**The negative-space sentence** (for the Overview):
> "There are no <thing>, no <other thing>, no <third thing>."

Examples:
- "There are no decorative borders, no gradients, no patterns, no shadows."
- "No second chromatic color. No atmospheric gradients. No spotlight cards."

These sentences are powerful because they explicitly enumerate what's absent — agents respond to lists.

**The contagious detail sentence** (one specific, unusual fact about the brand):
> "<Brand> uses <specific technique> — <explanation>."

Examples:
- "Vercel uses `box-shadow: 0px 0px 0px 1px rgba(0,0,0,0.08)` — a zero-offset, zero-blur, 1px-spread shadow that creates a border-like line without the box model implications."
- "Stripe enables OpenType `\"ss01\"` globally on all sohne-var text — a custom stylistic set that defines the brand's letterforms."
- "Linear treats Display and Text as one continuous voice; the family change is silent."

## Things to avoid

**Filler adjectives** — "modern", "clean", "sleek", "professional", "polished", "elegant". These describe nothing. Replace with specific facts.

**Marketing-speak** — "delights users", "industry-leading", "thoughtfully crafted". Out of voice for this format.

**Vague comparisons** — "feels premium", "looks high-end", "has a luxurious feel". Specify which concrete decisions create the perception.

**Overclaiming with "always" / "never"** — unless the brand actually enforces it. "All headlines are weight 300" is false if even one isn't. Hedge appropriately ("primarily 300", "the dominant headline weight is 300").

**Apologetic gaps** — "Hopefully this captures…", "We tried to…". Just state what was extracted and what wasn't.

## A test for whether your prose is good enough

After drafting a section, ask: **could an agent reading only this section produce something visually correct without the rest of the file?**

For Overview: yes — it should standalone-explain canvas, voltage, and one distinguishing fact.
For Colors: yes — every color has a role and a use.
For Typography: yes — every role has size + weight + letter-spacing + use.
For Components: yes — every component has its tokens and one place it appears.
For Do's/Don'ts: yes — each rule is concrete enough to act on.
For Agent Prompt Guide: yes — each example prompt is copy-pasteable.

If the answer is "kind of" or "the agent would need to ask follow-ups", the section is underwritten.
