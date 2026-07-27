<div align="center">

# Mobile App

**One skill for taking mobile products from a fuzzy idea to a trustworthy release.**

[![Agent Skill](https://img.shields.io/badge/Agent_Skill-mobile--app-6D5EF8)](skills/mobile-app/SKILL.md)
[![Codex Plugin](https://img.shields.io/badge/Codex-skill--only_plugin-111827)](.codex-plugin/plugin.json)
[![Version](https://img.shields.io/badge/version-1.0.0-16A34A)](CHANGELOG.md)
[![License](https://img.shields.io/badge/license-proprietary-F59E0B)](LICENSE)

</div>

Mobile App is a reusable agent skill for planning, designing, building, auditing, and improving iOS, Android, and cross-platform products. It connects product decisions, interface quality, engineering discipline, sustainable growth, and user trust in one working system.

## What it covers

| Area | Typical work |
| --- | --- |
| Product | Positioning, category analysis, MVP scope, roadmaps, metrics, experiments |
| Experience | Journeys, navigation, screens, forms, search, accessibility, motion |
| Revenue | Onboarding, trials, paywalls, subscriptions, purchases, cancellation |
| Engagement | Retention, notifications, progress, rewards, sharing, ethical safeguards |
| Engineering | Architecture, state, offline behavior, security, testing, performance, release |
| AI | Recommendations, generation, assistants, agents, approvals, recovery, evaluation |

The skill can start from a prompt, inspect an existing repository, review a product flow, or carry a feature from strategy through implementation and release checks.

## Example prompts

```text
Use $mobile-app to turn this idea into the smallest coherent MVP and delivery plan.
```

```text
Use $mobile-app to audit this app's onboarding, paywall, retention loops, and cancellation flow.
```

```text
Use $mobile-app to design and implement offline-first search for this mobile codebase.
```

```text
Use $mobile-app to review this AI assistant feature for trust, approval, recovery, and evaluation gaps.
```

## Install

Licensed users can install the skill with the open Agent Skills CLI:

```bash
npx skills add HarishChandran3304/mobile-app --skill mobile-app
```

The standalone skill lives at [`skills/mobile-app`](skills/mobile-app). The repository is also packaged as a skill-only Codex plugin through [`.codex-plugin/plugin.json`](.codex-plugin/plugin.json), so it can be distributed through a Codex plugin marketplace without changing the runtime skill.

## How it is organized

```text
mobile-app/
├── .codex-plugin/
│   └── plugin.json
├── skills/
│   └── mobile-app/
│       ├── SKILL.md
│       ├── LICENSE.txt
│       ├── agents/
│       │   └── openai.yaml
│       └── references/
│           ├── product-and-measurement.md
│           ├── experience-and-interface.md
│           ├── onboarding-and-monetization.md
│           ├── engagement-and-ethics.md
│           ├── engineering-and-release.md
│           └── ai-and-agentic.md
├── CHANGELOG.md
├── LICENSE
└── README.md
```

`SKILL.md` is the operating layer. It classifies the request, selects only the relevant references, inspects available product or code context, and drives the work toward a concrete artifact or implementation. The reference files provide focused depth without loading the entire package into every task.

## Compatibility

- Codex and ChatGPT through the included plugin manifest
- Codex and other agents that support the Agent Skills format
- Existing iOS, Android, React Native, Flutter, and cross-platform repositories

## Licensing

This repository is source-available and proprietary. Public access does not grant usage or redistribution rights. See [LICENSE](LICENSE) and open a repository issue to discuss personal, team, or commercial licensing.
