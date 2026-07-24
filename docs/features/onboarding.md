# Onboarding — Feature Specification

## Overview

The onboarding flow is the single most critical UX in FocusPath. It must explain why the app needs system-level permissions, build trust with ADHD users who are rightly skeptical of new tools, and get the user to their first "win" within 90 seconds — all without triggering the abandonment patterns that kill ADHD tools.

## Design Principles (from research)

1. **Explain before asking** — every permission request is preceded by a plain-language "why"
2. **Progressive disclosure** — don't show everything at once; reveal complexity as needed
3. **Contextual triggering** — only ask for permissions when the user is about to use that feature
4. **Always skippable** — every step has a "skip for now" option
5. **Show progress** — user always knows where they are in the flow
6. **No walls of text** — short sentences, clear headings, visual cues
7. **First win fast** — user should feel a benefit within 90 seconds of opening the app

## Onboarding Flow (v1)

### Screen 1: Welcome (5 seconds)
```
┌──────────────────────────────────────┐
│                                      │
│         👋 Hey there!                │
│                                      │
│    I'm your FocusPath buddy.         │
│    I'll help you stay on track       │
│    without being annoying about it.  │
│                                      │
│         [  Let's go!  ]              │
│                                      │
│    Step 1 of 4                       │
└──────────────────────────────────────┘
```
- Buddy character waves from corner
- One button. No decisions. No configuration.
- Visual: warm, minimal, friendly

### Screen 2: The Deal (15 seconds)
```
┌──────────────────────────────────────┐
│                                      │
│   Here's the deal:                   │
│                                      │
│   ✅ I'll help you focus             │
│   ✅ I'll block distracting sites    │
│   ✅ I'll remind you about tasks     │
│                                      │
│   ❌ I'll never lock you out         │
│   ❌ I'll never guilt you            │
│   ❌ I'll never share your data      │
│                                      │
│         [  Sounds good  ]            │
│          [  Skip tour  ]             │
│                                      │
│    Step 2 of 4                       │
└──────────────────────────────────────┘
```
- Sets expectations and builds trust
- "Skip tour" for users who want to dive in
- Buddy nods along with each promise

### Screen 3: The Permission (30 seconds)
```
┌──────────────────────────────────────┐
│                                      │
│   To block distracting sites,        │
│   I need to update one system file.  │
│                                      │
│   📁 What: Your computer's "hosts"   │
│           file (it's like a phone    │
│           book for the internet)     │
│                                      │
│   🎯 Why: So I can redirect          │
│           distracting sites back to  │
│           your computer instead      │
│                                      │
│   🔒 Safety: I'll back up the        │
│              original file first.    │
│              You can quit me anytime │
│              to undo everything.     │
│                                      │
│         [  Grant access  ]           │
│          [  Skip for now  ]          │
│                                      │
│    Step 3 of 4                       │
└──────────────────────────────────────┘
```
- **This is the trust-critical screen**
- Plain language, no technical jargon
- Specific: what, why, safety
- Buddy looks earnest/sincere
- "Skip for now" is essential — no forced permissions
- After clicking "Grant access" → OS permission prompt appears

### Screen 4: First Win (30 seconds)
```
┌──────────────────────────────────────┐
│                                      │
│   Let's set up your first task!      │
│                                      │
│   What's ONE thing you want to       │
│   get done today?                    │
│                                      │
│   [___________________________]      │
│                                      │
│   How long will it take?             │
│                                      │
│   ○ 15 min  ○ 30 min  ● 1 hour      │
│   ○ 2 hours  ○ I'm not sure         │
│                                      │
│         [  Start focus block  ]      │
│                                      │
│    Step 4 of 4                       │
└──────────────────────────────────────┘
```
- User creates their first task — immediate value
- Simple: one task, time estimate, one button
- After this: buddy minimizes to corner, focus block starts
- **First win achieved within ~80 seconds**

### Post-Onboarding: Progressive Feature Introduction

After the 4-step flow, features are introduced contextually:

| Trigger | Introduction |
|---------|-------------|
| First distraction detected | "I can block sites like this. Want to set that up?" |
| Task completed | "Nice! Want to see your focus stats?" |
| End of day | "Want me to help plan tomorrow?" |
| 3 days of use | "I can learn your patterns if you want. Optional." |
| First missed day | "Hey! No worries. Ready to jump back in?" |

## Permission Trust Architecture

### The Permission Credibility Ladder

Not all permissions are equal. Order matters:

1. **App detection** (low sensitivity) — "I can see which app you're using to help you focus"
2. **Notifications** (medium sensitivity) — "I can remind you about tasks"
3. **Hosts-file access** (high sensitivity) — the one that needs the most explanation

### How to Explain Elevated Permissions

Bad: "FocusPath needs administrator privileges."
Good: "I need permission to update one system file so I can help you avoid distracting websites. Here's exactly what happens when you say yes..."

### Trust Signals Throughout

- **Open source badge**: "You can read every line of my code on GitHub" (link)
- **Privacy promise**: "Nothing leaves your computer unless you choose to connect an AI key"
- **Reversible**: "You can undo everything by quitting me from the system tray"
- **No account**: "I don't even have a server. Everything lives on your machine."

## What NOT To Do

- ❌ "Create your account" — no accounts, ever
- ❌ "Choose your plan" — no monetization in onboarding
- ❌ "Connect your calendar" — optional, contextual, never forced
- ❌ Walls of text explaining every feature
- ❌ "You're all set! Here are 47 settings to configure."
- ❌ Streak-shaming language ("Don't break your streak!")

## v1 MVP Scope

- [ ] 4-screen onboarding flow as specified
- [ ] Permission explanation card before OS prompt
- [ ] "Skip for now" on every screen
- [ ] Buddy character present and animated throughout
- [ ] First task creation as final screen
- [ ] Post-onboarding contextual feature introduction (app detection only)

## v2 Enhancements

- [ ] Interactive tutorial (buddy guides through first focus block)
- [ ] "Import from other apps" optional step
- [ ] Extended permissions explanation for camera (if v3 pursued)
- [ ] A/B testable onboarding variants
