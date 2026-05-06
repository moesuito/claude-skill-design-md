# design-md — a Claude Code skill

> Distill any visual identity into a `DESIGN.md` an AI agent can build pixel-consistent UI from — and ship a paired `design-showcase.html` so humans can see it without running a server.

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Skill: Claude Code](https://img.shields.io/badge/Claude_Code-Skill-7C3AED.svg)](https://docs.anthropic.com/en/docs/claude-code/skills)

## What it does

`DESIGN.md` is a single markdown file that captures a brand's visual identity — color tokens, typography scale, components, do's and don'ts — in a format optimized for LLM reading. It sits beside `AGENTS.md` / `CLAUDE.md` (which say *how* to build) and tells the agent *how it should look*.

This skill turns any of these inputs into a finished `DESIGN.md` + `design-showcase.html` pair:

- A live URL (`stripe.com`, `linear.app`, etc.)
- A brand book PDF or style guide
- Screenshots of an existing product
- A mood-board description ("Linear meets Notion")

```
my-project/
├── DESIGN.md              ← what AI agents read to build pixel-consistent UI
└── design-showcase.html   ← what humans open to see the system at a glance
```

The HTML showcase is a single self-contained file. No fetch, no server, no JS deps beyond Google Fonts via CDN — just double-click and view.

## Quick example

Ask Claude Code:

> *"Create a DESIGN.md for stripe.com"*
> *"Build a DESIGN.md from this brand guide PDF I attached"*
> *"Capture this brand's identity: [URL]"*

Claude invokes the skill, runs through the 6 phases below, and drops two files in your project root.

Then:
- An AI agent opens `DESIGN.md` and builds in-brand UI on the first try.
- You open `design-showcase.html` in any browser to inspect colors, typography, components, and directives without spinning up tooling.

## How it works

The skill runs in 6 phases:

| Phase | What happens |
|---|---|
| 1 | Extract raw values — hex, fonts, radii, spacing — from the source identity |
| 2 | Name tokens semantically (role-based, not literal: `colors.canvas`, not `colors.white`) |
| 3 | Pick the canonical canvas + brand voltage (the one accent the brand defends) |
| 4 | Write the prose — opinionated, comparative, with explicit scarcity rules and Don'ts |
| 5 | Assemble & lint the `DESIGN.md` |
| 6 | Generate the paired `design-showcase.html` from the same tokens |

The prose voice is non-negotiable: specific not generic, comparative ("where most AI brands use cool blue, this one uses warm cream"), and full of named anti-patterns. See `references/writing-voice.md` for the full guide.

## Two output formats

`DESIGN.md` ships in either of the two formats from the `awesome-design-md` corpus:

- **Frontmatter format** (default — newer, ~60% of corpus): YAML token graph + prose. Tokens reference each other via `{token.refs}` interpolation. Used by Linear, Claude, Notion, Apple, Nike.
- **Numbered format** (older — ~40% of corpus): pure markdown, 9 numbered sections, hex inline. Used by Stripe, Vercel, Tesla.

The skill picks frontmatter by default and switches to numbered when the brand is heavy on editorial / photography rather than systematized tokens.

## Installation

This is a [Claude Code](https://claude.com/claude-code) skill. Drop it into your skills folder:

```bash
# macOS / Linux
git clone https://github.com/moesuito/claude-skill-design-md ~/.claude/skills/design-md

# Windows (PowerShell)
git clone https://github.com/moesuito/claude-skill-design-md $env:USERPROFILE\.claude\skills\design-md
```

Restart Claude Code (or run `/skills`) and you're done. Trigger phrases:

- "create a DESIGN.md"
- "extract design system from [URL/file]"
- "DESIGN.md from this site"
- "capture this brand"
- "make design tokens for an AI agent"
- "Stitch DESIGN.md"
- "awesome-design-md style"

## File map

```
design-md/
├── SKILL.md                            ← skill orchestrator (read by Claude Code)
├── README.md                           ← this file
├── LICENSE                             ← Apache 2.0
├── references/
│   ├── frontmatter-format.md           ← spec for the YAML+prose format
│   ├── numbered-format.md              ← spec for the 9-section pure-prose format
│   ├── writing-voice.md                ← how to write prose that steers an agent
│   └── showcase-format.md              ← spec for the paired HTML showcase
└── templates/
    ├── frontmatter.md                  ← fillable skeleton for frontmatter format
    ├── numbered.md                     ← fillable skeleton for numbered format
    └── showcase.html                   ← complete worked example showcase
                                          (Sequora Post Production — adapt per brand)
```

## Quality bar

A finished `DESIGN.md` should let an agent that has never seen the brand:

- Pick the right canvas color on the first try.
- Pick the right primary CTA color on the first try.
- Use the right font weight at display sizes (e.g. Stripe is 300, not 700).
- Apply the correct border radius (Linear is 8px; Stripe is 4–8px; Notion uses pills).
- Avoid the brand's anti-patterns (no second accent, no pill CTAs where forbidden, no neutral gray shadows where the brand uses tinted ones).

If those five tests don't pass, the skill goes back and adds more prose voice — generic AI output produces generic AI UI.

## Credits

This skill is built on top of the `DESIGN.md` format and ecosystem:

- **[awesome-design-md](https://github.com/VoltAgent/awesome-design-md)** — the canonical corpus of `DESIGN.md` files, curated by the [VoltAgent](https://github.com/VoltAgent/voltagent) team. The format conventions, the role-based token naming, the writing-voice patterns, and the section structure all come from that corpus. The live preview gallery at [getdesign.md](https://getdesign.md) is the visual reference for the showcase HTML.
- **[Google Stitch](https://stitch.withgoogle.com/)** — pioneered the `DESIGN.md` format as a brand-identity artifact LLMs could consume directly.

The included `templates/showcase.html` uses **Sequora Post Production** as a complete worked example (a real brand the author worked with). It's structurally portable to any brand — the skill's Phase 6 documents how to adapt it.

## License

Apache 2.0 — see [LICENSE](LICENSE).

You can use, modify, fork, and redistribute this skill freely, including for commercial work. If you ship a derivative, keep the attribution.

## Contributing

Issues and PRs welcome. Particularly useful contributions:

- Additional showcase template variants (light-canvas, photography-first, editorial)
- Format spec refinements based on new patterns observed in the awesome-design-md corpus
- Better defaults for brands that don't define semantic colors / spacing scales / etc.
- Translations of `SKILL.md` and `references/*` into other languages

## Author

Built by [João Alano](https://github.com/moesuito) for the Claude Code skills ecosystem.
