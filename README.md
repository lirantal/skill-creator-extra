# skill-creator-extra

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](skills/skill-creator-extra/SKILL.md)
[![Works with Claude Code](https://img.shields.io/badge/Claude%20Code-skill-blueviolet)](https://claude.ai/code)

A Claude Code skill that turns a working skill draft into an excellent one.

The official skill creator handles drafting and evals. This picks up where it leaves off — adding the structure, positioning, and architecture that make a skill actually useful.

---

## What it fixes

| Problem | What this skill does |
|--------|----------------------|
| Skill reads like docs, not a workflow | Redesigns around concrete use-cases with verify/repeat loops |
| Claude rarely triggers the skill | Rewrites the description with outcome-first, trigger-phrase-rich copy |
| Instructions are vague or passive | Enforces imperative form and explains the *why* behind each step |
| SKILL.md is bloated and hard to follow | Applies progressive disclosure — moves domain detail into `references/` |

---

## Usage

Just say it naturally in Claude Code:

```
"Help me make a skill for X"
"Review my SKILL.md"
"Turn this workflow into a skill"
```

The skill runs the official creator first, then applies 6 enhancement phases automatically.

---

## What a good description looks like

```yaml
# Before
description: Runs Snyk CLI commands across four scanning domains and generates reports.

# After
description: >
  Finds and fixes security vulnerabilities in your project without you directing
  every step. Use this skill when the user says "scan for vulnerabilities",
  "fix security issues", "check my Dockerfile", or "run a security audit" —
  even if they don't mention Snyk by name.
```

---

## Install

Add to your Claude Code project:

```bash
claude skill add https://github.com/lirantal/skill-creator-extra
```

---

## License

Apache-2.0 © [lirantal](https://github.com/lirantal)

---

## Author

skill-creator-extra © Liran Tal, Released under the Apache-2.0 License.
