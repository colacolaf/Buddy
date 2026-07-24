# AI Buddy — Feature Specification

## Overview

The Buddy is the core differentiator and retention engine of FocusPath. It is an always-on-top animated character that lives in the corner of the user's screen, serving as a virtual body-double, productivity companion, and the primary interface for the app.

## Design Rationale

Research is unanimous: ADHD users prefer **conversational interfaces** over dashboards. Apps like Goblin.tools succeed specifically because they feel like utilities you pull out when stuck, not systems you have to maintain. The Buddy personifies this — it's not a feature of the app; it IS the app.

## Core Behaviors

### Always-On-Top Presence
- Lives in one screen corner (user-configurable: bottom-right default)
- Small footprint (~120x120px default, expands on interaction)
- Semi-transparent when idle, opaque when active
- Never steals focus from active work
- Clickable to expand for interaction

### App/Activity Detection
- Tracks active window title and process name via OS APIs
- Classifies apps as: Productive, Neutral, or Distracting (user-configurable)
- Monitors keyboard activity within active windows
- Detection is local-only — no data leaves the machine

### Emotional State System

The Buddy has distinct emotional states tied to user behavior:

| State | Trigger | Behavior |
|-------|---------|----------|
| **Idle/Neutral** | Default, user on task | Gentle idle animation, subtle breathing/pulse |
| **Focused/Proud** | Extended productive session detected | Confident posture, occasional thumbs-up, "You're crushing it" |
| **Concerned** | Distracting app detected >2 minutes | Head tilt, gentle nudge: "Hey, noticed you're on Reddit — chem chapter waiting?" |
| **Strict** | Third distraction in a session | Arms crossed, firmer tone: "Bold move. You've got 2 tasks due today." |
| **Celebratory** | Task marked complete or Done List milestone reached | Victory animation, confetti, "TASK COMPLETE! That's the one that mattered today!" Also fires on Done List milestones: "3 tasks done! Look at your Done List growing!" |
| **Welcoming** | App opened after absence | Warm wave: "Hey! Ready to jump back in?" — NEVER guilt |
| **Gentle** | Multiple tasks missed, user override used | Smaller posture, softer voice: "Rough day. Want to just do one tiny thing?" |

### Personality Calibration

The Buddy adapts its strictness based on:
- **After override used**: Next day starts with stricter confirmation requirements
- **After all tasks completed**: Next day starts friendlier, with celebratory callbacks
- **After multiple missed days**: Resets to gentle/welcoming — no accumulated guilt
- **Time of day**: More direct during designated focus hours, relaxed in evenings

## Interaction Model

### Buddy Initiates
- Distraction detection → gentle nudge (never interrupts active typing)
- Scheduled task approaching → "Chem study starts in 10 minutes"
- Task overdue → "Still planning to study for chem today?"
- Achievement unlocked → celebration
- Done List milestone → "You've completed 3 tasks today! That's a streak!" (fires at 1, 3, 5, 10 completed tasks)
- Shame-Free Reset triggered → Buddy acknowledges fresh start: "All cleared. Clean slate. Ready to set one thing for today?"

### User Initiates
- Click buddy → expand to interaction panel
- Type/talk to buddy → natural language input
- Quick actions: "Start focus block" / "Mark task done" / "Snooze for 30min"

## Technical Architecture

```
┌─────────────────────────────────┐
│         Electron Main           │
│  ┌──────────────────────────┐   │
│  │   Active Window Tracker  │   │
│  │   (OS-level APIs)        │   │
│  └──────────┬───────────────┘   │
│             ↓                   │
│  ┌──────────────────────────┐   │
│  │   Activity Classifier    │   │
│  │   (rules + user config)  │   │
│  └──────────┬───────────────┘   │
│             ↓                   │
│  ┌──────────────────────────┐   │
│  │   Emotion State Machine  │   │
│  │   + Animation Controller │   │
│  └──────────┬───────────────┘   │
│             ↓                   │
│  ┌──────────────────────────┐   │
│  │   Buddy Renderer         │   │
│  │   (transparent overlay)  │   │
│  └──────────────────────────┘   │
└─────────────────────────────────┘
```

## Animation System

- **Idle**: Subtle breathing, occasional blink, head turn
- **Transitions**: Smooth morphing between emotional states (CSS transforms + sprite sheet)
- **Celebrations**: Particle effects (confetti, sparkles) triggered on task completion
- **Nudge**: Gentle bounce + speech bubble appearing
- **Seasonal themes**: Buddy gets visual makeovers every 6-8 weeks (winter, space, cyberpunk)

## Privacy

- All window tracking is local-only
- App classification rules stored locally in SQLite
- No keystroke logging — only activity/no-activity binary detection
- User can pause buddy detection at any time
- Clear visual indicator when buddy is "watching" (eyes open/closed metaphor)

## v1 MVP Scope

- [ ] Always-on-top transparent window
- [ ] 3 emotional states (idle, concerned, celebratory)
- [ ] Basic idle + nudge animations
- [ ] Active window title detection
- [ ] Hardcoded productive/neutral/distracting classification
- [ ] Speech bubble notifications
- [ ] 10 voice lines across states
- [ ] Done List milestone celebrations (1, 3, 5, 10 tasks)
- [ ] Shame-Free Reset acknowledgment response

## v2 Enhancements

- [ ] Full emotional state machine (all 7 states)
- [ ] Adaptive strictness calibration
- [ ] Full animation library
- [ ] Seasonal themes
- [ ] User voice line preferences
- [ ] BYOK AI-powered natural language interaction
