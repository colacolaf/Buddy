# Buddy Architecture — Technical Specification

> **Decision**: Hybrid algorithmic + AI (BYOK). Pre-written responses for triggered events, LLM for open-ended chat.
> **Status**: Approved via Counsel review. See §5 for adversarial evaluation.

---

## 1. Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│                   Buddy System                       │
│                                                      │
│  ┌──────────────────┐    ┌──────────────────────┐   │
│  │  Algorithmic Core │    │   AI Chat Layer       │   │
│  │  (always active)  │    │   (user-initiated)    │   │
│  │                   │    │                       │   │
│  │ • Trigger detection│   │ • BYOK API key        │   │
│  │ • Emotion state   │    │ • Open-ended dialog   │   │
│  │   machine         │    │ • Task decomposition  │   │
│  │ • Pre-written     │    │ • Complex reasoning   │   │
│  │   response library│    │ • Natural language    │   │
│  │ • Animation queue │    │                       │   │
│  │ • Speech bubbles  │    │ • Falls back to       │   │
│  │                   │    │   algorithmic if no   │   │
│  │  LATENCY: <50ms   │    │   API key configured  │   │
│  │  COST: Free       │    │                       │   │
│  │  OFFLINE: Yes     │    │  LATENCY: 500ms-3s    │   │
│  └────────┬──────────┘    │  COST: User's API key │   │
│           │               │  OFFLINE: No          │   │
│           └───────┬───────┘                       │   │
│                   ↓                                │   │
│  ┌──────────────────────────────────────────────┐  │   │
│  │           Response Orchestrator               │  │   │
│  │  • Routes trigger → algorithmic or AI        │  │   │
│  │  • Merges character personality layer        │  │   │
│  │  • Queues animation + speech bubble          │  │   │
│  │  • Enforces master prompt constraints        │  │   │
│  └──────────────────────────────────────────────┘  │   │
└─────────────────────────────────────────────────────┘
```

## 2. Hybrid Routing Logic

### When to use Algorithmic (pre-written)

| Trigger | Response Source | Why |
|---------|----------------|-----|
| Distraction detected | Pre-written library | Must respond in <50ms — latency breaks ADHD flow |
| Task completed | Pre-written library | Celebration is predictable, fast dopamine hit |
| Focus block starting | Pre-written library | Standardized ritual, no AI needed |
| Scheduled reminder | Pre-written library | Time-sensitive, must fire exactly on time |
| Daily planning ritual | Pre-written library | Structured flow with fixed questions |
| Emotional state transitions | Pre-written library | Idle→Concerned→Strict transitions are rule-based |
| Streak/achievement notification | Pre-written library | Fixed triggers with known data |

### When to use AI (LLM via BYOK)

| Trigger | Response Source | Why |
|---------|----------------|-----|
| User opens chat & types | LLM | Open-ended, user expects conversation |
| "Help me figure out why I can't focus" | LLM | Requires empathy + reasoning + personalization |
| Task decomposition request | LLM | Complex reasoning about task structure |
| Goal planning session | LLM | Multi-turn, context-heavy, adaptive |
| User is upset/frustrated | LLM | Needs genuine empathetic response, not scripted |
| "What should I work on?" | LLM | Requires calendar + goal + history synthesis |

### Automatic Fallback

If no API key configured:
- AI-required triggers silently downgrade to algorithmic
- Chat mode shows: "I can chat smarter with an API key — it's optional and stays on your machine. [Learn more]"
- All core buddy functions work without AI

## 3. Pre-Written Response Library Structure

```
src/buddy/responses/
├── master-constraints.ts    # Shared rules all responses must follow
├── triggers/
│   ├── distraction.ts       # "Hey, noticed you're on [app]..."
│   ├── task-complete.ts     # "TASK CRUSHED! That was the one!"
│   ├── focus-start.ts       # "Focus block starting. Need anything?"
│   ├── focus-end.ts         # "Block done. Solid session."
│   ├── reminder.ts          # "[Task] starts in [time]"
│   ├── planning.ts          # Daily ritual question flow
│   ├── override.ts          # "Alright, I'll hold you to it tomorrow"
│   ├── welcome-back.ts      # "Hey! Ready to jump back in?"
│   ├── bad-day.ts           # "Rough one. Want to just do one tiny thing?"
│   └── idle.ts              # Ambient observations, occasional check-ins
├── characters/
│   ├── sage-cat.ts          # Cat-specific response variants
│   ├── scout-dog.ts         # Dog-specific response variants
│   ├── atlas-human.ts       # Human-specific response variants
│   └── kitsu-fox.ts         # Fox-specific response variants
└── animations/
    ├── idle.ts
    ├── transitions.ts
    └── celebrations.ts
```

Each trigger file exports: `{ variants: string[], characterOverrides: Record<CharacterId, string[]> }`

## 4. Response Selection Algorithm

```typescript
interface BuddyResponse {
  text: string;
  emotion: EmotionState;
  animation: AnimationType;
  duration: number; // ms to display
  priority: number; // higher = overrides current display
}

function selectResponse(
  trigger: TriggerType,
  character: CharacterId,
  context: UserContext
): BuddyResponse {
  // 1. Get base response variants for this trigger
  const variants = responseLibrary[trigger].variants;

  // 2. Get character-specific override if available
  const charVariants = responseLibrary[trigger].characterOverrides[character];

  // 3. Select variant using anti-repetition algorithm
  //    (never show same variant twice in a row, weighted random)
  const selected = antiRepeatSelect(charVariants ?? variants, context.recentHistory);

  // 4. Map to emotion state + animation based on trigger type
  const { emotion, animation } = triggerToEmotionMap[trigger];

  // 5. Apply master constraints (strip anything violating rules)
  const sanitized = applyMasterConstraints(selected);

  return { text: sanitized, emotion, animation, duration: calcDuration(sanitized), priority: triggerPriority[trigger] };
}
```

**Anti-repetition**: Each character has 5-8 variants per trigger. The system tracks the last 20 responses and weights selection against recent variants. A variant cannot repeat within 5 interactions of the same trigger type.

## 5. The Counsel — Adversarial Review of Buddy Architecture

### Scorecard

| Dimension | Score (1–10) | Note |
|---|---|---|
| Latency (ADHD-critical) | 9 | Algorithmic core is <50ms. AI chat has latency but is user-initiated — acceptable |
| Cost sustainability | 9 | Algorithmic is free. AI is user-funded via BYOK. Zero operational cost to maintainer |
| Engagement resilience | 7 | 5-8 variants per trigger per character × anti-repetition = ~6-12 months before detectable patterns. Seasonal refreshes add longevity |
| Privacy integrity | 8 | Algorithmic is fully local. AI chat is BYOK — user controls their data pipeline |
| Offline functionality | 8 | Core buddy works fully offline. Only AI chat requires internet |
| Implementation complexity | 7 | Two response paths to build. Response library is labor-intensive (40-60 lines per trigger × 9 triggers × 4 characters = ~1,800 lines) but straightforward |
| Hallucination risk | 8 | Algorithmic has zero risk. AI chat is contained to user-initiated mode where expectation of fallibility is set |
| Personality consistency | 6 | **Warning**: Two response sources (algorithmic + AI) could produce inconsistent personality. Needs strong character prompt enforcement in AI path |

### Binding Constraint: Personality Consistency (6)

The hybrid approach creates a risk: the algorithmic buddy says X in the cat's aloof style, but the AI chat responds in a different tone. This is the "split personality" problem flagged by research. **Mitigation**: The AI system prompt must include the EXACT character personality definitions from the algorithmic library, and the response orchestration layer must post-process AI responses to match the character's speech patterns.

### Verdict: Proceed

Hybrid algorithmic + AI is the correct architecture for this use case. The binding constraint (personality consistency) has a straightforward mitigation. No fatal flaws.

### Confidence: 85%

High confidence — this is a well-understood pattern (Duolingo uses it, Goblin.tools uses it). The risk is in execution quality of the response library, not architectural soundness.

---

## 6. Emotion State Machine

```
                    ┌─────────┐
          ┌────────→│  IDLE   │←────────┐
          │         └────┬─────┘         │
          │              │               │
     no activity    distraction      app opened
      for 30min     detected         after absence
          │              ↓               │
          │         ┌─────────┐         │
          │    ┌───→│CONCERNED│───┐     │
          │    │    └────┬─────┘   │     │
          │    │         │         │     │
          │  3rd     user     2nd       │
          │  distract returns  distract  │
          │    │    to task    │         │
          │    ↓         │    ↓         │
          │ ┌──────┐    │ ┌────────┐   │
          │ │STRICT│    │ │WELCOME │   │
          │ └──┬───┘    │ │ BACK   │   │
          │    │         │ └───┬────┘   │
          │  task         │    │        │
          │  complete     │  planning   │
          │    ↓          │  complete   │
          │ ┌──────────┐  │    │        │
          └─┤CELEBRATORY│  │    │        │
            └─────┬─────┘  │    │        │
                  │         │    │        │
                  └─────────┴────┴────────┘
                       (return to IDLE)
```

### State Transitions

| From | Trigger | To | Cooldown |
|------|---------|----|----------|
| IDLE | Distracting app >2min | CONCERNED | — |
| CONCERNED | User returns to task | IDLE | 5min before re-trigger |
| CONCERNED | 2nd distraction | CONCERNED (escalated) | — |
| CONCERNED | 3rd distraction | STRICT | — |
| STRICT | Task completed | CELEBRATORY | — |
| CELEBRATORY | Celebration complete | IDLE | — |
| ANY | App opened after >4hr absence | WELCOME BACK | Once per day |
| WELCOME BACK | Planning ritual complete | IDLE | — |
| ANY | User override used | CONCERNED (marked "override") | Next day modifier |
| ANY | Focus block timer ends | CELEBRATORY or IDLE (depends on task status) | — |
| IDLE | 30min no activity | IDLE (gentle check-in) | 30min |
| ANY | Multiple tasks missed | GENTLE | Once per day |

---

## 7. Response Library Size Requirements

### Per Trigger, Per Character

| Trigger | Minimum Variants | Recommended Variants |
|---------|-----------------|---------------------|
| Distraction detected | 6 | 10 |
| Task complete | 5 | 8 |
| Focus block start | 4 | 6 |
| Focus block ended | 4 | 6 |
| Scheduled reminder | 5 | 8 |
| Daily planning | 6 | 10 |
| Override used | 4 | 6 |
| Welcome back | 5 | 8 |
| Bad day / gentle | 4 | 8 |
| Idle observations | 8 | 15 |

**Total library**: ~2,000-2,500 lines across 4 characters, 10 trigger types

Characters share the same trigger structure but vary in:
- Word choice and sentence length
- Emotional expression style
- Metaphors and references
- Animation mappings
- Idle observation themes

---

## 8. AI Chat Mode Specification

### When Activated
- User clicks buddy to expand panel
- User types in chat input
- User says "hey buddy" or equivalent wake phrase (future: voice)

### System Prompt Structure
```
[MASTER PROMPT - shared constraints]
[CHARACTER PROMPT - personality layer]
[USER CONTEXT - injected dynamically]
  - Current tasks
  - Today's goals
  - Recent activity
  - Calendar events
  - Current emotional state
[CONVERSATION HISTORY - last 10 turns]
```

### Input Guardrails
- Max response length: 150 words (ADHD-friendly)
- Must include exactly ONE actionable suggestion per response
- Must NOT: suggest disabling FocusPath, override blocking without permission, give medical advice
- Tone must match character personality

### Fallback Behavior
If API call fails or times out (>5s):
- Buddy says: "Brain freeze! Let me try that differently..." 
- Retries once with simplified prompt
- If still fails: "My thinking cap is glitching. Want to try a quick action instead?" + shows quick action buttons
