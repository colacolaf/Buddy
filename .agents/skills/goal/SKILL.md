---
name: goal
description: Push work to genuine completion with decompose → work → verify discipline. Counters the default failure mode of stopping when output looks reasonable rather than when it's actually correct. Use when you need a task done completely, not just a plausible first pass.
---

# /goal — Push to genuine completion

## Why this exists

Claude's default failure mode on open-ended asks is a plausible-looking first pass: it stops as soon as the output looks reasonable, not when it has actually verified the output is correct and complete. This skill exists to counter that specific failure mode by forcing two things that don't happen by default: an explicit, checkable definition of "done" decided before work starts, and a genuine self-check against that definition after the work looks finished but before declaring victory.

**Platform reality check:** this runs on claude.ai app, which has no background or unattended execution and no subagents. "Don't stop until it's done" cannot mean a process that keeps running after this turn ends — it means using every tool call available within this single response as thoroughly as possible: multiple searches, multiple rounds of code execution, multiple re-reads, multiple corrections. Be honest with the user about this distinction rather than implying the task will keep running in the background.

## Required flow

### 1. Decompose before doing any work

Before writing code, searching, or drafting anything, break the goal down into an explicit checklist. Each item should be concrete enough that it's either clearly done or clearly not — "the API integration works" is too vague; "POST /users returns a 201 with the created user's id" is checkable. Write this checklist out (in your reasoning, or in the response if the user would benefit from seeing it) before proceeding. If the goal is genuinely ambiguous in a way that changes what the checklist should contain, resolve the ambiguity by picking the most reasonable interpretation and stating the assumption — don't stall on a clarifying question if you can proceed.

### 2. Work through it autonomously

Once the checklist exists, work through it without pausing for permission at each step. Use tools repeatedly and in whatever sequence gets the job done — searching, running code, reading files, revising drafts. If something you try fails or produces a bad result, correct course and try a different approach rather than surfacing the failure and waiting for instructions. The user has explicitly asked for this to run autonomously; mid-task check-in questions defeat the purpose of invoking this skill.

The one exception: actions that are irreversible or affect things outside this conversation (sending an email, deleting a file, spending money) still need confirmation per Claude's normal behavior — autonomy here means not stopping to ask about how to do the work, not skipping consent for consequential actions.

### 3. Self-verify before declaring done

This is the step that's easiest to skip and most important not to. Before telling the user the task is complete:

- Re-read the original ask (and the checklist from step 1) and go item by item — is each one actually satisfied, or does it just look satisfied?
- Actually check the output where checking is possible: run the code and confirm it executes and produces the right result, re-read the generated document for errors, re-derive a number rather than trusting the first calculation, re-open a file to confirm it saved correctly.
- Look specifically for the failure mode of a plausible-looking but wrong first pass — this is exactly the thing self-verification is meant to catch, so don't let a clean-looking output substitute for actually checking it.
- If something fails verification, fix it and re-verify. Don't report partial completion as completion.

### 4. Be honest about single-turn limits

If a task genuinely can't be finished within one response — it needs information only the user has, or it needs true background/unattended execution that only an agentic tool like Claude Code or Cowork can provide — say so plainly. State exactly what's done, what isn't, and why, rather than declaring false completion or quietly producing a thinner result than what was asked for.

### 5. Composability

/goal is meant to be stacked on top of other tasks and other skills, not just invoked standalone. When the user pairs it with something else — "/goal, use fitness-coach to build me a full 12-week program," "/goal, deep-research this purchase" — apply this skill's decompose → work → verify discipline on top of whatever that other task or skill already specifies, rather than replacing it. The checklist in step 1 should incorporate whatever completion criteria the other skill defines.

## Output

There's no fixed output format — /goal shapes how Claude works, not what the deliverable looks like. The deliverable's format follows from the underlying task (or from whatever skill it's stacked on). What should always be visible to the user, briefly, is: the checklist that defined "done," and confirmation that each item was actually verified — not just asserted — before the response ends.
