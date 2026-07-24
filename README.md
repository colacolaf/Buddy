# FocusPath

> A free, open-source native desktop app that helps people with ADHD stay on task — built by someone who lives the problem.

FocusPath combines an AI buddy companion, system-wide distraction blocking, task-gated unlocks, an intelligent calendar, and a 60-second daily planning ritual — all local-first and privacy-respecting.

## Why FocusPath?

Existing ADHD tools are either expensive ($39–$199/yr), missing key features, or designed for neurotypical brains. FocusPath is:

- **Free & open source** — no paywall, read the code yourself
- **Buddy-first** — an always-on-screen AI companion, not a sterile dashboard
- **Task-gated, not time-gated** — unlock distractions by completing tasks, not waiting out timers
- **Forgiveness-designed** — no guilt, no shame, just gentle accountability
- **Evidence-backed** — built on implementation-intention research, body-doubling science, and ADHD community input

## Current Status

**Phase: Pre-development research & planning**

- [x] Deep research on ADHD needs and existing tools
- [x] Competitive analysis
- [x] Full adversarial review (The Counsel)
- [x] Feature specifications written
- [ ] Milestone 0: Community trust validation
- [ ] Milestone 0.5: Electron proof-of-concept

## Documentation

All specs and research in [`/docs`](docs/):

| Document | Description |
|----------|-------------|
| [Full Report](docs/full-report.md) | Research synthesis, Counsel review, refined plan |
| [AI Buddy](docs/features/buddy.md) | Corner companion with emotional states and animations |
| [System Blocking](docs/features/blocking.md) | Cross-platform blocking with escalating friction |
| [AI Calendar](docs/features/calendar.md) | Intelligent scheduling with task decomposition |
| [Onboarding](docs/features/onboarding.md) | ADHD-friendly onboarding and permission flow |
| [Goals](docs/features/goals.md) | Implementation-intention goal setting |
| [Planning Ritual](docs/features/planning-ritual.md) | 60-second daily micro-planning |

## Tech Stack

- **Shell**: Electron + TypeScript
- **UI**: React
- **Data**: SQLite (better-sqlite3)
- **AI**: BYOK (Bring Your Own Key) — user provides OpenAI/Anthropic API key
- **Platforms**: Mac + Windows

## Design Principles

1. **Friction, not walls** — escalating friction with deliberate unlock, never a hard block
2. **Task-gating over time-gating** — ADHD time blindness makes timers useless
3. **Forgiveness-first** — no streaks that shame, no guilt for missed days
4. **Buddy is the architecture** — the companion is the interface, the retention engine, the moat
5. **Conversational over dashboard** — buddy asks questions, surfaces info; menus are secondary
6. **Explain before asking** — every permission request preceded by plain-language "why"
7. **AI is enhancement, not requirement** — buddy works fully without AI
8. **Local-first, BYOK for cloud** — no FocusPath servers, user controls their AI

## License

TBD — evaluating MIT, GPL, and AGPL. Core will be free forever. Advanced features may be paid in the future (stated transparently from day one).

---

*Built with AI-assisted coding by someone who lives the ADHD experience. Questions, contributions, and feedback welcome.*
