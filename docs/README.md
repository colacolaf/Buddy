# FocusPath — Documentation

> A native desktop app that helps people with ADHD stay on task — built by someone who lives the problem, open-sourced for others to use and contribute.

## Docs Index

### Planning & Strategy
| Document | Description |
|----------|-------------|
| [Full Report](full-report.md) | Complete research synthesis, Counsel adversarial review, and refined project plan |

### Buddy System ⭐
| Document | Description |
|----------|-------------|
| [Buddy Architecture](buddy/buddy-architecture.md) | Technical architecture: hybrid algorithmic + AI, emotion state machine, routing logic, Counsel review |
| [Buddy Characters](buddy/buddy-characters.md) | Four companion designs: Sage (cat), Scout (dog), Atlas (human), Kitsu (fox spirit) |
| [Master System Prompt](buddy/buddy-master-prompt.md) | Shared foundational prompt — ADHD-aware constraints, interaction protocols, non-negotiables |
| [Sage (Cat)](buddy/buddy-prompts/sage-cat.md) | Character prompt: aloof, composed, dry wit |
| [Scout (Dog)](buddy/buddy-prompts/scout-dog.md) | Character prompt: enthusiastic, loyal, warm |
| [Atlas (Human)](buddy/buddy-prompts/atlas-human.md) | Character prompt: steady, grounded, relatable |
| [Kitsu (Fox)](buddy/buddy-prompts/kitsu-fox.md) | Character prompt: clever, playful, wise mischief |

### Features
| Document | Description |
|----------|-------------|
| [AI Buddy (legacy)](features/buddy.md) | Original buddy feature spec — superseded by buddy/ docs above |
| [System Blocking](features/blocking.md) | Cross-platform site/app blocking with escalating friction and task-gated unlock |
| [AI Calendar](features/calendar.md) | Intelligent scheduling with task decomposition and adaptive rescheduling |
| [Onboarding](features/onboarding.md) | ADHD-friendly onboarding flow, permission explanation, trust-building |
| [Goals](features/goals.md) | Implementation-intention goal setting and breakdown |
| [Planning Ritual](features/planning-ritual.md) | 60-second daily planning ritual for ADHD users |

## Quick Links

- **Philosophy**: [Design Principles](full-report.md#design-principles)
- **Research**: [Evidence Base](full-report.md#research-synthesis)
- **Roadmap**: [Milestone Plan](full-report.md#milestone-breakdown)
- **Risks**: [Risk Register](full-report.md#risks-and-mitigations)
- **Competitors**: [Market Analysis](full-report.md#competitor-landscape)

## Stack

- **Shell**: Electron + TypeScript
- **UI**: React
- **Data**: SQLite (better-sqlite3)
- **AI**: Hybrid local + user-provided API key (BYOK)
- **License**: TBD (MIT/GPL/AGPL)
