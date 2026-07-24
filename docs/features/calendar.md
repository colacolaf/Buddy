# AI Calendar — Feature Specification

## Overview

An intelligent calendar that accepts natural language input, decomposes vague tasks into specific scheduled blocks, adapts when plans change, and always asks before committing. The AI is powered by the user's own API key (BYOK model) — no FocusPath cloud infrastructure.

## Design Rationale

ADHD users struggle with:
- **Time blindness**: Can't estimate how long tasks take or visualize the day
- **Initiation friction**: "Study for chem" is too vague to start
- **Rigid plans**: Life happens, and missed blocks create guilt spirals

The calendar addresses all three: AI handles estimation and decomposition, natural language removes input friction, adaptive rescheduling eliminates guilt.

## Core Flow

### Adding an Event/Task

**User says/inputs**: "I need to study for my chemistry exam on Friday"

**AI responds with questions** (not assumptions):
1. "What chapters/topics are on the exam?"
2. "What grade are you aiming for?"
3. "How comfortable are you with the material right now? (1-10)"
4. "When do you usually focus best? Morning, afternoon, or evening?"

**AI proposes a schedule**:
```
Based on your answers, here's a plan:

Mon 7pm-8pm: Review chapters 1-3 (core concepts)
Tue 7pm-8pm: Chapters 4-6 practice problems
Wed 6pm-7pm: Review weak areas, practice exam
Thu 7pm-8pm: Final review, summary sheet

I moved your usual gaming time from 7pm-8pm to 8pm-9pm on those days.
Does this work?
```

**User**: Can review, adjust, or approve. Nothing is committed until confirmed.

### Missed a Scheduled Block

**AI detects** (via buddy activity tracking): scheduled chem study time passed with no activity.

**Buddy asks**: "Missed chem study at 7. Want me to reschedule?"

**If yes**: AI finds next available slot that fits the remaining study plan. "I moved it to tomorrow at 6pm. You'll still finish before Friday."

**If no**: Block is marked as skipped. No guilt. No broken streak. Just... skipped.

**When multiple blocks accumulate** (3+ missed in a row): Buddy offers Shame-Free Reset: "You've missed a few. Want me to clear the overdue blocks and start fresh? No questions asked." This archives all missed events and resets the schedule to a clean slate.

### Conflict Detection

**User adds**: "Dentist appointment Tuesday at 7pm"

**AI checks**: "That conflicts with your chem study block. Want me to move chem to Wednesday at 6pm instead?"

**User options**:
- Accept reschedule
- Keep dentist, cancel chem (AI will suggest makeup)
- Move chem manually

## Task Decomposition Engine

### How It Works

1. **Input**: Vague task ("study for chem exam")
2. **AI breakdown**: Decomposes into specific, time-estimated sub-tasks
3. **Calendar placement**: Finds open slots matching the user's focus preferences
4. **Approval**: User reviews and confirms the full plan

### Decomposition Examples

| Input | AI Output |
|-------|-----------|
| "Study for chem exam Friday" | 4 sessions: review chapters, problems, weak areas, final review |
| "Write history essay due next week" | Research (2hrs) → Outline (1hr) → Draft (3hrs) → Edit (1hr), spread across available slots |
| "Clean my room" | Pick up trash (10min) → Put away clothes (15min) → Vacuum (10min) → Wipe surfaces (5min) |
| "Apply to 3 internships" | Find listings (1hr) → Tailor resume (1hr) → Write cover letters (2hr) → Submit (30min) |

### Goal-Aware Scheduling

When a task is linked to a goal (see `goals.md`), the AI:
- Prioritizes goal-linked tasks over standalone tasks
- Asks about grade/outcome targets to calibrate effort
- Schedules more time for goals with approaching deadlines
- Surfaces goal progress in buddy interactions

## Adaptive Rescheduling

### Rules
- **Never double-book**: Always proposes alternatives before overwriting
- **Respect focus preferences**: Schedules difficult tasks during user's best hours
- **Buffer time**: 15-minute gaps between blocks (configurable)
- **Energy-aware**: Lighter tasks after heavy blocks
- **Weekend protection**: Doesn't fill weekends unless user asks

### What Happens When...
| Scenario | AI Response |
|----------|-------------|
| Task missed | Propose reschedule to next available slot |
| Two tasks missed | Ask if priorities changed; offer to drop lowest-priority |
| Three+ tasks missed | Offer Shame-Free Reset: "Want to archive the overdue ones and start clean?" |
| All tasks missed | Buddy goes gentle: "Rough day. Want to try just one thing tomorrow?" |
| Deadline approaching | Escalating-but-gentle urgency: "Chem exam in 3 days. You've done 2 of 4 sessions." |
| User is sick/busy | "Snooze all" option pushes everything back proportionally |
| Event completed on time | Populates the Done List on the dashboard with task name and completion time |

## Natural Language Processing

Supported input patterns:
- "Study chem Tuesday at 7pm for 2 hours"
- "I need to finish my essay by Friday"
- "Remind me to call mom at 3pm"
- "Move my 7pm study block to tomorrow"
- "Add dentist appointment next Tuesday at 2pm"
- "I'm going to the gym every MWF at 6am"

## BYOK AI Architecture

```
┌──────────────┐     API Key     ┌──────────────────┐
│  FocusPath   │ ──────────────→ │  OpenAI/Anthropic │
│  (local)     │ ←────────────── │  (cloud)          │
└──────────────┘    Response     └──────────────────┘

- User provides their own API key
- FocusPath sends: task text, calendar context, goal context, user preferences
- Cloud returns: structured schedule proposal
- All data stays in transit only — nothing stored on FocusPath servers
- Falls back to manual calendar entry without API key
```

### Without AI Key
- Calendar works manually (drag-and-drop, natural language date parsing)
- Task decomposition is template-based (pre-built breakdown patterns)
- Buddy still provides reminders and nudges
- "AI features available with your own API key" shown non-intrusively

## Data Model (SQLite)

```sql
CREATE TABLE calendar_events (
  id TEXT PRIMARY KEY,
  title TEXT NOT NULL,
  description TEXT,
  start_time INTEGER NOT NULL,
  end_time INTEGER NOT NULL,
  is_all_day BOOLEAN DEFAULT 0,
  is_recurring BOOLEAN DEFAULT 0,
  recurrence_rule TEXT,
  linked_goal_id TEXT,
  linked_task_id TEXT,
  is_ai_generated BOOLEAN DEFAULT 0,
  status TEXT DEFAULT 'scheduled', -- scheduled, completed, missed, skipped
  completed_at INTEGER, -- timestamp used to populate Done List on dashboard
  created_at INTEGER,
  updated_at INTEGER
);

CREATE TABLE task_decompositions (
  id TEXT PRIMARY KEY,
  parent_event_id TEXT,
  step_number INTEGER,
  title TEXT NOT NULL,
  estimated_minutes INTEGER,
  is_completed BOOLEAN DEFAULT 0,
  FOREIGN KEY (parent_event_id) REFERENCES calendar_events(id)
);
```

## v2 MVP Scope

- [ ] Basic calendar view (week + day)
- [ ] Manual event creation with natural language date parsing
- [ ] Task decomposition (template-based, no AI)
- [ ] Calendar-sourced tasks appear in buddy's daily planning
- [ ] Basic reminders (time-based)

## v2 Full Scope

- [ ] BYOK AI integration
- [ ] Full natural language input
- [ ] AI task decomposition engine
- [ ] Adaptive rescheduling
- [ ] Goal-aware scheduling
- [ ] Conflict detection and resolution
- [ ] Recurring events
- [ ] Calendar export (ICS)
