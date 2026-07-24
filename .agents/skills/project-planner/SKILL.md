---
name: project-planner
description: Define scope, resources, and ordered milestone breakdowns before building anything. Produces a concrete definition of done, out-of-scope items, and a sequenced plan with explicit dependencies. Use before starting any coding project, DIY build, or side-hustle.
---

# Project Planner

## Why this exists

Jumping straight into building something — code, a physical project, a side hustle — without first defining scope tends to produce either scope creep (the project never feels done because "done" was never defined) or a plan that looks like a flat task list with no sense of what depends on what. This skill exists to do the upfront thinking that makes the actual build go smoothly: a real definition of done, a resource list, and an ordered sequence of milestones with dependencies called out.

This skill is deliberately not the same thing as /goal. project-planner produces the plan; /goal is the discipline that executes a plan to genuine completion. Keep them separate — don't fold execution-completion logic into this skill.

## Required flow

### 1. Clarify scope before any implementation talk

Before discussing how to build anything, establish:

- What does "done" actually look like for this project? A concrete, checkable definition, not a vague sense of direction.
- What's explicitly out of scope? Naming what won't be included is often more useful than naming what will, since it's what prevents scope creep later.

If the person's initial description doesn't make this clear, ask — this is exactly the kind of ambiguity worth resolving before proceeding, since the shape of the whole plan depends on it.

### 2. Fit the project to its shape

Different project types need different milestone patterns — don't force everything into a generic template:

- **Coding projects:** architecture/design → build → test → ship
- **DIY / physical builds:** materials & tools → build → finish/test
- **Side-hustle / business projects:** validate the idea → build → launch

Identify which shape (or blend of shapes) the project actually is before drafting milestones, since this determines what order things need to happen in.

### 3. Identify concrete resources

Name the actual tools, materials, libraries, or skills the project will need — specifically, not generically ("a saw and 2x4s," not "some tools"). If the domain is unfamiliar enough that this list would otherwise be a guess, that's exactly the situation the deep-research skill is for — note that it can be invoked to fill in real knowledge gaps rather than guessing at what's needed.

### 4. Build an ordered milestone breakdown, not a flat list

The output should be a sequence, not a checklist with no structure. Flag dependencies explicitly — "milestone 3 can't start until milestone 2's materials arrive" or "the API needs to be stable before the frontend integration begins" — so the person can see not just what needs doing but what order it needs doing in and why.

### 5. Hand off to /goal

Once a project is scoped, the natural next step is execution. End by explicitly offering to run /goal on the resulting plan (or a specific milestone from it) to actually push it to completion — this skill stops at the plan, /goal is what carries it out.

## Output

A markdown artifact works well for most project plans — scope statement, resource list, and an ordered milestone breakdown with dependencies noted — since it's a reference document the person will come back to across multiple building sessions, not something they'll only read once in chat.
