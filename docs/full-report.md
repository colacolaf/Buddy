# FocusPath — Full Report

*Refined project plan incorporating deep research, 19-angle adversarial interrogation, and a full Counsel review.*

---

## 1. Research Synthesis

### 1.1 The Core Problem

ADHD productivity tools universally suffer from **abandonment after novelty fades**. The root cause is a design mismatch: most tools assume neurotypical executive function (daily maintenance, rigid structures, delayed rewards), while ADHD brains operate on **interest-based motivation** requiring low-friction entry, immediate feedback, forgiveness for bad days, and zero-maintenance design.

### 1.2 Evidence-Backed Strategies

| Strategy | Evidence | Implementation |
|----------|----------|----------------|
| **Implementation intentions** | Meta-analysis (PMC8149892): "if-then" plans significantly close intention-action gap | Goal feature forces specificity: "read chapter 4, 7pm, at desk" |
| **Body doubling** | ACM 2024 study: presence of another person generates accountability | The buddy serves as a persistent virtual body-double |
| **Structured planning rituals** | PMC6406620: habits and routines are the most effective coping strategy | 60-second daily micro-plan on app open |
| **Externalized cognitive load** | Systematic review (PMC11278469): offloading executive function to tools | Buddy handles scheduling, decomposition, reminders |
| **Task-gating over time-gating** | ADHD time blindness makes timers ignorable | Unlock based on "mark task done," not "minutes passed" |

### 1.3 Why Existing Tools Fail

1. **Shame-based mechanics** — broken streaks trigger avoidance, not motivation
2. **Setup high → maintenance drag** — dopamine from building the system, not using it
3. **No immediate feedback** — long feedback loops don't motivate ADHD brains
4. **Time blindness unaddressed** — rigid alarms interrupt hyperfocus or get ignored
5. **Feature overkill** — the system becomes the procrastination
6. **Hard blocks cause panic** — being trapped triggers anxiety and uninstalls

### 1.4 What ADHD Communities Actually Want

- **Conversational interfaces** over dashboards and menus
- **Zero-maintenance** — tools that work without daily upkeep
- **"Emergency utilities"** not "systems of record" — pull out when stuck, not live in daily
- **Forgiveness-first design** — no guilt for missed days, easy restart
- **Low-cost, privacy-focused** — many effective tools are prohibitively expensive

### 1.5 Competitor Landscape

| Tool | Type | Price | Key Gap |
|------|------|-------|---------|
| Freedom | Cross-device blocker | $8.99/mo | No task system, no buddy, expensive |
| Cold Turkey | Desktop blocker | $39 one-time | Desktop only, no task-gating, no AI |
| Forest | Gamified focus timer | Free/$1.99 | Timer-based (time blindness problem), mobile-focused |
| Tiimo | Visual planner | Subscription | Visual timeline but no blocking |
| Sunsama | Daily planner | $16/mo | Great ritual, very expensive, no blocking |
| Focusmate | Body doubling | Free/$5/mo | Requires scheduling, human-dependent |
| Inflow | CBT coaching | $199/yr | High cost, no blocking features |

**FocusPath's gap**: Free + open source + buddy accountability + task-gated blocking + AI calendar + planning ritual — an integrated suite no single competitor offers, at zero cost.

---

## 2. The Counsel — Adversarial Review

### Scorecard

| Dimension | Score (1–10) |
|---|---|
| Problem-solution fit | 9 |
| Competitive differentiation | 8 |
| Feature alignment with evidence | 9 |
| Abandonment resistance | 7 |
| **Technical feasibility (scope)** | **4** ⚠️ |
| **Distribution & adoption** | **5** ⚠️ |
| Privacy/trust design | 7 |
| Monetization/sustainability | 6 |
| Timeline reality | 6 |
| Risk management | 7 |

**Binding constraints**: Technical feasibility (4) and Distribution (5).

### Recommendation: Proceed with Caution

No fatal flaws. Mitigations required before committing to full native-app build:

1. **Build a 2-week Electron PoC** before architecture lock-in
2. **Run Milestone 0** — validate trust/permission barrier with r/ADHD
3. **Commit to scope path** based on PoC velocity data

### Confidence: 72%

Would rise with positive trust validation + PoC velocity data. Would drop if community rejects permissions or PoC reveals 3x scope.

---

## 3. Refined Design Principles

1. **Friction, not walls.** Escalating friction with deliberate unlock. Never an unremovable hard block.
2. **Task-gating over time-gating.** Gate on "mark this done," not "25 minutes passed."
3. **Forgiveness-first.** No streaks that shame. No guilt for missed days. Fresh start is one click.
4. **Buddy is the architecture, not a feature.** The buddy is the retention engine, the interface, and the emotional core.
5. **Conversational over dashboard.** Buddy asks questions, surfaces information. Menus are secondary.
6. **Explain before asking.** Every permission request preceded by plain-language "why this is needed."
7. **AI is enhancement, not requirement.** Buddy works fully without AI. AI adds intelligence, not basic function.
8. **Local-first, BYOK for cloud.** No FocusPath servers. User brings own API key for AI features.
9. **Free core forever.** Advanced features may be paid in the future — stated transparently from day one.

---

## 4. Feature Specifications

| Feature | v1 | v2 | v3 |
|---------|----|----|-----|
| AI Buddy (corner, animated, emotional states) | ✅ Core | ✅ Expanded animations | ✅ |
| App/site detection (active window tracking) | ✅ | ✅ | ✅ |
| System-wide blocking (hosts-file) | ✅ | ✅ | ✅ |
| Escalating friction alerts | ✅ | ✅ | ✅ |
| Task-gated unlock (partial tiers + override + stricter buddy) | ✅ | ✅ | ✅ |
| Basic usage dashboard | ✅ | ✅ Expanded | ✅ |
| 60-second daily planning ritual | ✅ Minimal | ✅ Full guided | ✅ |
| AI calendar + task decomposition | — | ✅ | ✅ |
| Implementation-intention goals | — | ✅ | ✅ |
| Body doubling mode | — | ✅ | ✅ |
| Webcam phone detection | — | — | ✅ Opt-in module |
| BYOK AI integration | ✅ | ✅ | ✅ |

### Detailed feature specs: see `/docs/features/`

---

## 5. 10-Layer Abandonment Prevention System

1. **Buddy emotional attachment** — parasocial accountability; miss the buddy, not the app
2. **Streak system WITH freezes** — 2-3 freezes/month prevent "all-or-nothing" quit
3. **Forgiveness-first restart** — "Ready to jump back in?" — never "You missed 14 days"
4. **Variable reward drops** — mystery buddy animations/themes after tasks
5. **Seasonal novelty refresh** — buddy gets new themes every 6-8 weeks
6. **Escalating-but-gentle urgency** — information, not guilt, as deadlines approach
7. **Micro-task decomposition** — AI breaks tasks into 5 tiny steps
8. **Body doubling mode (v2+)** — live focus rooms with other users
9. **Set-it-and-forget-it automation** — recurring schedules, no daily decisions needed
10. **Stricter-after-override loop** — manual override always available, but buddy tightens tomorrow

---

## 6. Architecture Decisions

### AI Model: BYOK (Bring Your Own Key)
- User provides OpenAI/Anthropic API key
- No FocusPath cloud infrastructure
- AI features degrade gracefully without key — buddy still works

### Buddy Personality
- **Default mode**: Warm, encouraging study partner
- **After task completion**: Celebratory, friendly, plays victory animations
- **During override**: Direct but not punitive — "Alright, I'll hold you to it tomorrow"
- **After multiple overrides**: Firmer tone, stricter confirmation requirements
- **On bad days**: Gentle, suggests smaller tasks instead of pushing

### Calendar AI Flow
1. User inputs goal/event in natural language or template
2. AI asks clarifying questions (deadline, desired grade, time estimate)
3. AI checks calendar for conflicts, proposes schedule
4. User approves or adjusts — nothing auto-committed
5. If task missed, AI reschedules to next available slot
6. One-click undo on any AI action

### Unlock Mechanic
1. **Partial tiers**: 1 task = 30min leisure. 2 tasks = 60min. All tasks = unrestricted.
2. **Manual override always available**: Typed-sentence commitment + 30-second delay
3. **Buddy gets stricter after override**: More confirmation steps tomorrow
4. **No hard walls ever**: User is never fully locked out

---

## 7. Milestone Breakdown (Refined)

### Milestone 0 — Validate trust barrier (1 week)
- Post to r/ADHD: "Would you trust a free OSS app with system-level permissions?"
- **Gate**: Don't proceed without real signal

### Milestone 0.5 — Electron PoC (2 weeks) ⭐ NEW
- Buddy window (always-on-top, basic animation)
- Active window detection
- Hosts-file blocking on ONE platform
- **Gate**: Measure actual hours. If >60 hours, pivot to web-first or buddy-only.

### Milestone 1 — Architecture & design (2 weeks)
- SQLite schema
- Cross-platform blocking approach (Windows + Mac)
- Figma wireframes (badge, dashboard, onboarding)
- Friction mechanic specification

### Milestone 2 — Core build v1 (6–8 weeks)
- Electron shell, onboarding flow with permission explanation
- System-wide blocking, usage tracking, alerts, friction unlock, task-gating
- Basic dashboard + always-on-top badge
- BYOK AI integration

### Milestone 3 — Test & ship v1 (2–3 weeks)
- Self-dogfood for 1 week minimum
- Recruit 10+ beta testers
- Code signing setup
- Public GitHub release

### Milestone 4 — v2 (6–8 weeks)
- Guided planning ritual, goals, calendar, adaptive reminders, expanded dashboard

### Milestone 5 — v3 (conditional)
- Camera companion as separate opt-in module

---

## 8. Risks and Mitigations

| Risk | Severity | Mitigation |
|------|----------|------------|
| Users won't grant system permissions | **Critical** | Milestone 0 tests this before code. Onboarding explains "why" before OS prompt. |
| Build scope 2-3x estimate | **Critical** | PoC checkpoint at M0.5. Pivot paths defined (web-first, buddy-only). |
| Unsigned app kills install rate | High | Budget code signing from M3. Open source builds trust. |
| Buddy doesn't prevent abandonment | High | Test core hypothesis cheaply (buddy-only PoC). 10-layer retention system as backup. |
| Windows/Mac blocking diverge | Medium | Researched in M1 before core build starts. |
| BYOK setup friction | Medium | Buddy works fully without AI. AI is enhancement only. |
| Open-source-then-monetize trust gap | Medium | State plan transparently in README from day one. |
| Solo developer bus factor | Medium | Public from day one. Contribution guide. Build community early. |
| Competitor feature response | Low | Buddy character + community is harder to clone than features. |

---

## 9. Action Items (Priority-Ordered)

1. **[This week]** Post to r/ADHD: trust/permission validation (Milestone 0)
2. **[This week]** Decide license (MIT vs GPL vs AGPL)
3. **[Week 1-2]** Build Electron PoC: buddy window + app detection + one-platform blocking
4. **[After PoC]** Commit to scope path: native / buddy-only / web-first
5. **[After PoC]** Write buddy personality spec — 20+ voice lines across emotional states
6. **[M1]** Research Windows vs Mac blocking approaches
7. **[M1]** Create Figma wireframes
8. **[M1]** Design SQLite schema
9. **[Ongoing]** Document everything publicly — the build process IS the college app story

---

## 10. College Application Framing

> "I identified a lived problem, researched what evidence-based ADHD tools actually do well, made a deliberate architectural bet to support features browser extensions can't offer, ran adversarial review against my own plan, and phased the build so I have something real and usable at each stage. The process of validating before building — asking the ADHD community whether they'd trust my app before writing a single line of code — demonstrates the kind of judgment I'll bring to everything I build."

---

*Report generated from: 6 deep research passes, 19-angle adversarial interrogation, full Counsel review. All claims sourced from research cited in individual feature docs.*
