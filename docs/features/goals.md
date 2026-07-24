# Goals — Feature Specification

## Overview

A goal-setting system that forces specificity through implementation-intention breakdown. Users can't just write "study more" — the system (via AI or templates) guides them to: what exactly, when, where, and the first concrete step.

## Design Rationale

Meta-analytic research (PMC8149892) confirms: implementation intentions ("if-then" plans) significantly close the gap between intention and action. "Study for chemistry" is weak. "Read chapter 4, 7pm, at my desk, with phone in other room" is strong.

The goal system bakes this specificity into the creation flow — it's not optional polish, it's the core mechanic.

## Goal Creation Flow

### AI-Assisted (with BYOK)

**User**: "I want to get an A in chemistry this semester."

**Buddy asks**:
1. "What's the first exam or deadline you're working toward?"
2. "What topics feel hardest right now?"
3. "When and where do you focus best?"
4. "What's getting in the way of studying right now?"

**AI produces**:
```
Goal: Get an A in Chemistry (Semester)
Deadline: December 15

Implementation plan:
├── Week 1-2: Chapters 1-3 Foundation
│   ├── Mon 7pm: Read Ch.1 + notes (at desk, phone away)
│   ├── Wed 7pm: Ch.1 practice problems (library)
│   └── Fri 4pm: Review weak spots (at desk)
├── Week 3-4: Chapters 4-6
│   └── ...
└── Week 5: Exam prep
    └── ...

First action right now: Open textbook to Chapter 1.
```
User approves or adjusts. Then tasks auto-populate the calendar.

### Template-Based (without AI)

User selects from templates:
- Academic goal (exam, project, semester)
- Habit goal (daily, weekly)
- Project goal (multi-step deliverable)
- Personal goal (fitness, creative, learning)

Each template has pre-built fields:
```
Goal title: ________________________
Target deadline: ___________________
Why this matters to me: ____________
First concrete step: _______________
Where I'll do it: _________________
When I'll do it: __________________
What might get in the way: _________
My plan to handle that: ___________
```

## Goal Dashboard (v2)

### Visual Representation
- Active goals shown as progress trees
- Each implementation step is a node
- Completed nodes turn green, grow leaves — and simultaneously populate the Done List on the dashboard
- Buddy tends the goal garden as metaphor
- Done List shows today's completed steps across all goals, providing a cross-goal view of progress

### Goal-Aware Calendar
- Calendar prioritizes goal-linked blocks
- Buddy nudges more persistently for goal-linked tasks
- Goal progress visible in daily planning ritual

### Streaks for Goals (forgiveness-designed)
- Track consecutive days of goal-related activity
- Streak freezes available (2-3/month)
- Breaking streak → buddy goes gentle: "Still got a B+ trajectory. Let's pick it back up."
- **Never shame-based**
- If a goal becomes overwhelming (multiple missed steps), buddy offers Shame-Free Reset: "Want to archive the past-due steps and reset this goal? The deadline stays, but the backlog clears."

## Implementation Intention Template

Every goal must produce answers to:

| Component | Example |
|-----------|---------|
| **What** exactly? | "Read Chemistry Chapter 4, sections 4.1-4.5" |
| **When** specifically? | "Tuesday at 7:00pm" |
| **Where**? | "At my desk, with phone in drawer" |
| **First step**? | "Open textbook to page 142" |
| **Obstacle**? | "Getting distracted by Discord notifications" |
| **If-then plan**? | "IF I feel the urge to check Discord, THEN I'll stand up and stretch for 30 seconds" |

## Goal Types

### Academic
- Exam preparation ("A in Chemistry final")
- Project completion ("History paper on French Revolution")
- Semester-long ("Maintain 3.5 GPA")

### Habit-Building
- Daily ("Meditate for 10 minutes")
- Weekly ("3 gym sessions")
- Breaking ("Under 30 min social media/day")

### Project
- Multi-step deliverables with dependencies
- Milestone tracking
- Deadline-driven progression

## Data Model (SQLite)

```sql
CREATE TABLE goals (
  id TEXT PRIMARY KEY,
  title TEXT NOT NULL,
  description TEXT,
  goal_type TEXT NOT NULL, -- academic, habit, project, personal
  target_outcome TEXT, -- "A in Chemistry", "3.5 GPA"
  deadline INTEGER,
  why_matters TEXT,
  status TEXT DEFAULT 'active', -- active, completed, abandoned
  created_at INTEGER,
  updated_at INTEGER
);

CREATE TABLE implementation_intentions (
  id TEXT PRIMARY KEY,
  goal_id TEXT NOT NULL,
  what TEXT NOT NULL,
  when_spec TEXT,
  where_spec TEXT,
  first_step TEXT,
  obstacle TEXT,
  if_then_plan TEXT,
  is_completed BOOLEAN DEFAULT 0,
  FOREIGN KEY (goal_id) REFERENCES goals(id)
);

CREATE TABLE goal_progress (
  id TEXT PRIMARY KEY,
  goal_id TEXT NOT NULL,
  date INTEGER NOT NULL,
  minutes_spent INTEGER DEFAULT 0,
  tasks_completed INTEGER DEFAULT 0,
  notes TEXT,
  FOREIGN KEY (goal_id) REFERENCES goals(id)
);
```

## v2 MVP Scope

- [ ] Goal creation with implementation-intention template
- [ ] Goal list view with basic progress
- [ ] Goal-linked calendar events
- [ ] Template library (academic, habit, project)

## v2 Full Scope

- [ ] AI-assisted goal breakdown (BYOK)
- [ ] Progress visualization (trees/garden)
- [ ] Goal-aware scheduling priority
- [ ] Streak tracking with freezes
- [ ] Goal-Buddy integration (buddy references your goals)
