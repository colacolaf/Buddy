# Daily Planning Ritual — Feature Specification

## Overview

A 60-second micro-planning ritual that runs when the user opens FocusPath (or at a scheduled time). Designed specifically for ADHD brains: minimal cognitive load, one key decision, zero guilt.

## Design Rationale

Research (PMC6406620) identifies structured routines as the most effective coping strategy for ADHD. But the key insight from the research: **the ability to restart is more important than the ability to maintain.** A 60-second ritual that you actually do is infinitely more effective than a 10-minute ritual you skip.

The ritual is designed around three principles:
1. **Orientation, not optimization** — see what's real, not build a perfect plan
2. **Single win** — one dopamine target, not a mountain of tasks
3. **Forgiveness** — skip a day? The ritual just runs the 60-second version next time

## The 60-Second Micro-Plan

### Step 1: Anchor (15 seconds)

**Buddy**: Shows today's calendar at a glance.
```
┌──────────────────────────────┐
│  Today: Tuesday, July 22     │
│                              │
│  📅 2pm - Dentist            │
│  📅 6pm - Dinner w/ friends  │
│                              │
│  2 events today.              │
│  5 free hours for tasks.     │
└──────────────────────────────┘
```
- Shows ONLY hard constraints (events with fixed times)
- Not a full task list — just what's non-negotiable
- Fixes time blindness: user knows what's actually taken

### Step 2: Single Win (30 seconds)

**Buddy**: "What's the ONE thing that would make today feel successful?"

```
┌──────────────────────────────┐
│                              │
│  What's your top task        │
│  for today?                  │
│                              │
│  [______________________]    │
│                              │
│  Suggested:                   │
│  📝 Chem Ch.4 practice       │
│     (from your Chem A goal)  │
│                              │
│  Or pick from today's list:  │
│  ○ History essay draft       │
│  ○ Email professor           │
│  ○ Clean room                │
│                              │
│       [  Lock it in  ]       │
│        [  Skip for now  ]    │
└──────────────────────────────┘
```
- Presents ONE primary question
- Surfaces goal-linked tasks first (priority)
- "Skip for now" always available
- If user has tasks from calendar, they appear as suggestions
- If no tasks exist, buddy asks: "Want to add one?"

### Step 3: Launch Check (15 seconds)

**Buddy**: "Ready to go? Here's what you need."
```
┌──────────────────────────────┐
│  Your focus block starts now:│
│                              │
│  🎯 Chem Ch.4 practice       │
│  ⏱  1 hour (until 3pm)      │
│                              │
│  You'll need:                 │
│  📖 Textbook page 142        │
│  ✏️ Notebook                  │
│  🧮 Calculator                │
│                              │
│  I'll block distractions      │
│  until 3pm. Ready?            │
│                              │
│       [  Start focus  ]       │
└──────────────────────────────┘
```
- Surfaces what the user needs for the task
- Confirms blocking activation
- One button to start

**Total time: ~60 seconds. One decision made. Focus block starts.**

## What If You Skip?

### The "Rescue Version"

If the user dismisses the ritual (or doesn't open the app in the morning):
- Buddy stays in neutral/idle state
- No guilt message. No "You missed planning!"
- Next time app opens (even at 4pm): runs the 60-second version
- Past tasks not completed? Auto-snoozed to tomorrow — no backlog shame

### After Multiple Missed Days
- Buddy: "Hey! Been a minute. Want to do a quick check-in?"
- If user says no: Buddy stays idle. No punishment.
- If user says yes: Runs the 60-second version
- The ritual NEVER accumulates backlog. Missed days are just... missed.

## Advanced Ritual (v2)

When the user has more time/energy, the buddy can offer an expanded version:

### Extended Ritual (3 minutes, optional)

1. **Yesterday recap** (30s): "Yesterday you completed 2 of 3 tasks." Shows the Done List from yesterday as positive reinforcement. Calls out what was completed before listing what carried over.
2. **Today's priorities** (60s): "You have 3 tasks. Which one matters most?"
3. **Timeboxing** (60s): Buddy suggests time blocks based on calendar availability
4. **Obstacle check** (30s): "Anything that might get in the way today?""

### Weekly Review (10 minutes, optional)
1. Goal progress check
2. Pattern insights ("You focus best 7-10pm on weekdays")
3. Adjust next week's schedule
4. Celebrate wins from the week

## Integration Points

- **Calendar**: Tasks auto-populated from calendar events
- **Goals**: Goal-linked tasks get priority in the "Single Win" suggestion
- **Buddy**: Buddy runs the ritual — it's a conversation, not a form
- **Done List**: Completed tasks from the ritual feed into the Done List on the dashboard — visible proof of progress throughout the day
- **Blocking**: Focus block starts immediately after ritual completion"

## Data Model

Planning ritual data is intentionally minimal:

```sql
CREATE TABLE daily_checkins (
  id TEXT PRIMARY KEY,
  date TEXT NOT NULL,
  top_task_id TEXT,
  focus_block_started BOOLEAN DEFAULT 0,
  ritual_completed BOOLEAN DEFAULT 0,
  created_at INTEGER
);
```

No streaks. No missed-day counters. Just a record of check-ins for patterns analysis (v2).

## v1 MVP Scope

- [ ] 3-step 60-second ritual on app open
- [ ] Calendar events surfaced in Anchor step
- [ ] Single Win: one task input with suggestions
- [ ] Launch Check: focus block starts from ritual
- [ ] Skip available at every step
- [ ] No backlog accumulation

## v2 Full Scope

- [ ] Extended ritual option (3-minute version)
- [ ] Yesterday recap with focus stats
- [ ] Timeboxing suggestions
- [ ] Obstacle check step
- [ ] Weekly review mode
- [ ] Pattern insights from check-in history
