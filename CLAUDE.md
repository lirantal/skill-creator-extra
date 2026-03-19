# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This repository contains **skill-creator-extra**, a Claude skill that layers structured enhancement phases on top of the official Claude skill creator plugin. It is a pure skill-definition repository with no build tooling, no package manager, and no test framework.

## Structure

```
skills/
└── skill-creator-extra/
    ├── SKILL.md          # The skill definition (frontmatter + instructions)
    └── references/       # Optional: domain-specific detail files loaded on demand
```

The single source of truth is `skills/skill-creator-extra/SKILL.md`. There is nothing to build, install, or test programmatically.

## Skill Architecture

The skill implements a **6-phase enhancement framework** that runs after the official Claude skill creator plugin produces a working draft:

| Phase | Focus |
|-------|-------|
| 1 | Run the official skill creator plugin first |
| 2 | Design use-cases with goal + numbered steps + done condition + verify/repeat loop |
| 3 | Validate frontmatter (`name`, `description`, `license`, `compatibility`, `metadata`) |
| 4 | Apply required body structure: heading → Instructions → Steps → Examples → Troubleshooting |
| 5 | Writing quality: imperative form, outcome-first positioning, no filler |
| 6 | Progressive disclosure: keep SKILL.md under 500 lines, move domain detail to `references/` |

## SKILL.md Format Rules

**Frontmatter (YAML)**
- `name`: kebab-case, must match the folder name exactly
- `description`: under 1024 characters, no XML tags (`<` or `>`), structured as [what it does] + [when to use] + [trigger phrases]
- `compatibility`: 1–500 characters describing environment requirements

**Body sections (required, in order)**
1. `# [Skill Name]` — top-level heading
2. `# Instructions` — signals where executable instructions begin
3. `### Step N: [name]` — numbered workflow steps
4. `## Examples` — 3–5 concrete scenarios using the `User says / Actions / Result` format
5. `## Troubleshooting` — failure modes using the `Error / Cause / Solution` format

**Progressive disclosure thresholds**
- SKILL.md body: target under 500 lines
- Reference files: place in `references/`, each with a table of contents if over 300 lines
- SKILL.md must explicitly state *when* to read each reference file, not just list them

## Key Design Principles

A great skill is a **workflow**, not a reference document. Every use-case must have:
- A stated goal (the outcome the user wants)
- Numbered, executable steps including an explicit `verify → repeat` loop
- A clear done condition Claude can check

The `description` field is the primary trigger mechanism. Write it "pushy": include the natural-language phrases users will actually say, lead with the outcome (not the mechanism), and add a clause telling Claude to trigger even if the skill isn't named explicitly.
