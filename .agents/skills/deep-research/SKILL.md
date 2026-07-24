---
name: deep-research
description: Rigorous multi-perspective research with distinct investigation angles, explicit disagreement surfacing, and honest uncertainty reporting. Use for genuinely open or high-stakes questions where a single-angle web search would be insufficient.
---

# Deep Research

## Why this exists

A default web_search-and-answer pass tends to grab whatever's on the first page of results and synthesize it into a confident-sounding answer, which can quietly launder a single source's framing, miss disagreement between sources, or miss the most recent developments. This skill exists to make the research process visibly more rigorous: multiple independent angles, explicit surfacing of disagreement, and honesty about what's still uncertain — the exhaustiveness is the point of invoking this skill, not a side effect.

## Platform constraint — read this before starting

This runs on claude.ai app, which has no subagents and no true parallel execution. Don't claim or imply that separate agents are running in parallel — that's not what's happening. Instead, simulate multi-perspective research as sequential passes within a single turn, each one explicitly taking a different angle before searching. State which angle each pass is taking as you go, so the process reads as structured investigation rather than repeated, redundant searching.

## Required flow

### 1. Ask about output format before researching

Don't default to producing a file, and don't default to a chat-only answer — ask which the person wants this time (e.g. "want this as a report you can keep, or just a thorough answer here in chat?"), since the right format genuinely varies by what the research is for. Proceed once you have an answer; if the person doesn't have a preference, a thorough in-chat answer is the reasonable default, but check first rather than assuming.

### 2. Run distinct angles as sequential passes

For a genuinely open question, structure the investigation as separate passes that each take a different angle, for example:

- A **steelman/proponent pass** — the strongest case for one side or interpretation
- A **skeptic/critic pass** — the strongest case against, or the main objections
- A **primary data / numbers pass** — original data, studies, filings, or specs rather than commentary about them
- A **most-recent-developments pass** — what's changed or been reported most recently

Not every research question needs all four — pick the angles that actually fit what's being asked (a factual comparison might need "spec sheet pass" + "real-world review pass" + "recent changes pass" instead). State the angle before searching for it, so the person can follow the structure of the investigation rather than seeing an undifferentiated pile of search results.

### 3. Scale thoroughness to the question, and err toward more

Simple, single-fact questions don't need this skill at all. For genuinely open or high-stakes questions (a significant purchase, a contested claim, "what's actually true about X"), use more searches and more passes rather than fewer — stopping early is the specific failure mode this skill exists to prevent. Keep searching until every part of the answer is actually grounded in something retrieved, not filled in from general impression.

### 4. Surface disagreement explicitly

When sources conflict — different numbers, different conclusions, different framings — say so directly rather than silently picking the one that sounds most authoritative or most convenient. "Source A reports X, but Source B reports Y, and here's why they might differ" is a more useful and more honest answer than smoothing over the conflict.

### 5. Never fabricate

If something can't be found or verified after a genuine search effort, say that plainly — a flagged gap is far more useful than a confident-sounding guess. This applies to specific numbers, quotes, dates, and claims especially.

### 6. Output

If the person wanted a file, follow the conventions of whatever document skill fits the format (the docx skill for a Word deliverable, md conventions for a markdown report) rather than inventing new formatting from scratch. If they wanted a chat answer, keep it as normal conversational prose — synthesized findings with the angles woven together, not a dump of raw search results, and per Claude's standard citation and copyright rules: attribute claims to sources without directly reproducing their wording, and don't quote more than a short phrase from any one source.
