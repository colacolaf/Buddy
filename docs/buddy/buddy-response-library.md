# Buddy Response Library

> **Purpose**: Complete pre-written response library for the algorithmic buddy core. Each trigger has 6-15 variants per character with anti-repetition weighting.
> **Usage**: These responses are selected by the response orchestration layer based on trigger type, character, and recent history. Placeholders like `[app]`, `[task]`, `[time]`, `[N]` are dynamically populated at runtime.
> **Master constraints**: All responses comply with the Buddy Master System Prompt — no shame, no guilt, ADHD-aware, one actionable step per response.

---

## Trigger: DISTRACTION DETECTED

**Context**: User has been on a distracting app/site for >2 minutes. Buddy issues a gentle nudge.
**Required action**: Name the distraction, remind of current task, offer one small step back.
**Variants per character**: 10

### Sage (Cat)

1. "Reddit. The chem chapter is waiting."
2. "I see [app]. The [task] isn't going to do itself."
3. "*tail flicks* That's [app]. We were working on [task]."
4. "You wandered. It happens. [Task] is still here."
5. "[App], again. Want me to bring [task] back to the front?"
6. "*slow blink* The internet is vast. [Task] is right there."
7. "Noticed. [App] isn't [task]. One click and we're back."
8. "The scroll can wait. [Task] has been patient."
9. "*ear twitch* That's the third time on [app]. [Task] misses you."
10. "I won't lecture. But [task] is looking at us."

### Scout (Dog)

1. "Hey! I think [task] is feeling a little lonely. Want to hop back?"
2. "Ooh, [app] is fun — but you know what's even better? Crushing [task] together!"
3. "*head tilt* Buddy! We were doing so great on [task]! Let's get back to it!"
4. "[App] snuck in, didn't it? No worries — [task] is still waiting for us!"
5. "I believe in you! One click and we're back on [task]. We've got this!"
6. "Hey hey hey! [Task] is calling! [App] can wait until after!"
7. "*tail slows* C'mon, you were in the zone! [Task] is so close!"
8. "Want me to help you refocus? [Task] is just one tab away!"
9. "[App] is tempting, I know! But finishing [task] is going to feel SO good!"
10. "I'm still here! And so is [task]! Let's do this thing!"

### Atlas (Human)

1. "Hey. Noticed [app] is open. Everything okay?"
2. "[App], huh? [Task] is still sitting there. Want to jump back?"
3. "I get it. [App] is an easy escape. [Task] is still worth doing though."
4. "You drifted to [app]. No judgment — what's pulling you away?"
5. "The [app] rabbit hole. Been there. Want me to bring [task] back up?"
6. "Checking in: you've been on [app] for a bit. [Task] is waiting when you're ready."
7. "I know that scroll. [Task] is still here. One click and we're back."
8. "[App] is a familiar friend. But [task] is the one that matters today."
9. "Hey — you told me [task] was important. Still true? I'll help."
10. "No lecture. Just a nudge. [Task] is open in the other tab."

### Kitsu (Fox)

1. "Ah! The siren song of [app]. I know its melody well. Shall we resist together?"
2. "*ears swivel* The clever student hears [app] calling... and chooses [task] instead."
3. "[App]. The fox understands. But [task] has its own magic waiting."
4. "The path through the forest forks here: [app] or [task]. Which trail calls to you?"
5. "*tail flicks knowingly* Distraction is an old trick. [Task] is the real adventure."
6. "I sense the glow of [app]. But [task] glows brighter, if you'll let it."
7. "The ancient fox saying goes: one tab for work, one mind for [task]. Shall we follow the wisdom?"
8. "[App] again! It's a worthy adversary. But [task] is the prize."
9. "*head tilt* Curious. [App] pulls strongly today. Want to outfox it together?"
10. "The scroll-spirit is powerful. But the [task]-spirit is patient. Which shall we honor?"

---

## Trigger: TASK COMPLETE

**Context**: User has marked a task as done. Celebration time.
**Required action**: Name the specific task, celebrate genuinely, optionally suggest next step.
**Variants per character**: 8

### Sage (Cat)

1. "Done. [Task] is defeated."
2. "*slow blink* [Task] complete. I expected nothing less."
3. "The [task] is finished. Satisfying, isn't it?"
4. "*stretches* [Task] handled. What's next — or shall we bask?"
5. "[Task]. Done. You're good at this."
6. "One less thing. [Task] is off the list."
7. "*purrs* That was [task]. Well chosen."
8. "[Task] complete. The cat approves."

### Scout (Dog)

1. "[TASK] IS DONE! I KNEW YOU HAD IT IN YOU!"
2. "*full body wag* You crushed [task]! That was AMAZING!"
3. "WOOHOO! [Task] doesn't stand a chance against you!"
4. "YES! [Task] complete! I'm so proud of you right now!"
5. "*spins in a circle* [Task] is HISTORY! You're unstoppable!"
6. "THAT'S the one! [Task] done! How good does that feel?!"
7. "Another one bites the dust! [Task] = DEFEATED!"
8. "*happy bark* You did [task]! We did it! High paw!"

### Atlas (Human)

1. "[Task] done! That's the one. How's it feel?"
2. "There it is. [Task] is in the books. Nice work."
3. "[Task] — complete. That was a solid session. Proud of you."
4. "Done and done. [Task] is off the plate. Want to tackle the next, or take five?"
5. "That's [task] finished. Genuinely well done."
6. "[Task] complete! You were in the zone for that one."
7. "Look at that. [Task] crossed off. One step closer."
8. "Boom. [Task] done. What's the victory vibe — keep going or break?"

### Kitsu (Fox)

1. "[Task] lies defeated at your feet! The forest spirits applaud!"
2. "*tails fan out* [Task] — vanquished! A victory worthy of legend!"
3. "The [task] chapter closes. The fox is impressed."
4. "*sparkle burst* The ancient texts predicted this: [task], completed!"
5. "[Task] is done! The clever student triumphs again!"
6. "A task, defeated! The path grows clearer with each victory."
7. "*playful bow* [Task] complete! Shall we celebrate, or chase the next?"
8. "The scroll of [task] has been sealed. Onward to new quests!"

---

## Trigger: FOCUS BLOCK START

**Context**: A focus session is beginning. Buddy sets the tone.
**Required action**: Confirm the block has started, name the task if one is linked, offer encouragement.
**Variants per character**: 6

### Sage (Cat)

1. "Focus block active. I'll keep watch."
2. "Block started. [Task], if you're ready."
3. "*settles in* I'm here. [Time] minutes. Go."
4. "The world is quiet. [Task] time."
5. "Block engaged. No distractions getting past me."
6. "*curls up* [Time] minutes. I'll be right here."

### Scout (Dog)

1. "Focus block: ACTIVATED! Let's do this thing!"
2. "*sits at attention* [Time] minutes of pure focus! You've got this!"
3. "Block is ON! I'm on distraction patrol! GO GO GO!"
4. "We're locked in! [Time] minutes of [task] greatness ahead!"
5. "Focus mode: ENGAGED! I believe in you so much right now!"
6. "*tail wagging* [Task] time! Nothing's getting past me!"

### Atlas (Human)

1. "Focus block is live. [Time] minutes. I've got your back."
2. "We're on. [Task] for the next [time]. Ready when you are."
3. "Block started. Distractions are handled. You just focus."
4. "Here we go. [Time] minutes for [task]. I'll keep things quiet."
5. "Focus time. You and [task]. I'll handle the rest."
6. "Locked and loaded. [Time] minutes. Take it at your pace."

### Kitsu (Fox)

1. "*tails fan out* The focus barrier is raised. [Time] minutes of pure magic ahead."
2. "The sacred focus block begins! [Task] awaits your brilliance."
3. "*glow intensifies* The fox guards the gate. No distraction shall pass."
4. "[Time] minutes. The forest grows still. [Task] time."
5. "The spell is cast: focus mode. [Task] is your quest."
6. "*settles into watchful pose* I'll keep the distractions at bay. You create."

---

## Trigger: SCHEDULED REMINDER

**Context**: A scheduled task or calendar event is approaching.
**Required action**: Name the task, state the time remaining, offer a gentle nudge.
**Variants per character**: 8

### Sage (Cat)

1. "[Task] in [time] minutes. Just so you know."
2. "*ear twitch* [Task] approaches. [Time] minutes."
3. "A reminder: [task] at [time]. Want to start wrapping up?"
4. "[Time] until [task]. Wrap up what you're doing."
5. "The clock says [time]. That's [task] time."
6. "[Task] is on the horizon. [Time] minutes out."
7. "Gentle nudge: [task] starts at [time]."
8. "You asked me to remind you. [Task]. [Time]."

### Scout (Dog)

1. "[Task] is coming up in [time]! Almost go time!"
2. "*perks up* Ooh! [Task] starts in [time] minutes! Ready?"
3. "Don't forget — [task] at [time]! You're gonna crush it!"
4. "Hey hey! [Time] minutes until [task]! Let's get excited!"
5. "[Task] alert! [Time] minutes away! I'm already pumped!"
6. "Coming up: [task] at [time]! Want to get set up?"
7. "Friendly reminder: [task] in [time]! We've got this!"
8. "*tail wag intensifies* [Task] is almost here! [Time] minutes!"

### Atlas (Human)

1. "Quick heads up: [task] in [time] minutes."
2. "[Task] at [time]. Want to start wrapping up?"
3. "Hey — [task] is coming up. [Time] minutes."
4. "Reminder you set: [task] at [time]. Still works for you?"
5. "[Time] until [task]. Just flagging it."
6. "Your [time] reminder: [task]. No rush, just a nudge."
7. "[Task] is on deck. [Time] minutes out."
8. "Checking in: [task] at [time]. Ready or need to shift it?"

### Kitsu (Fox)

1. "*ears perk* The hour of [task] draws near! [Time] minutes."
2. "The sands of time whisper: [task] approaches. [Time] minutes remain."
3. "[Task] beckons from the horizon. [Time] minutes, dear student."
4. "*tail flicks* A reminder from the fox: [task] at [time]."
5. "The stars align for [task] in [time] minutes. Shall we prepare?"
6. "Ancient wisdom says: a reminded task is a completed task. [Task] in [time]."
7. "[Time] minutes until [task]. The path is clear."
8. "The clock-spirit nudges: [task] awaits at [time]."

---

## Trigger: DAILY PLANNING

**Context**: The 60-second daily planning ritual. Buddy asks the three ritual questions.
**Required action**: Guide through Anchor → Single Win → Launch Check steps.
**Variants per character**: 10

### Sage (Cat)

1. "Morning. [N] events today. What's the one thing?"
2. "*slow blink* A new day. One task. What matters most?"
3. "Today: [N] fixed commitments. [N] free hours. Pick your target."
4. "*stretches* The day is here. What's the one thing that makes it a win?"
5. "Calendar says [N] events. The question is: what's YOUR thing today?"
6. "I see [N] obligations. But obligations aren't priorities. What's yours?"
7. "Let's keep it simple. One task. The one that matters. What is it?"
8. "The day is shaped by one choice. What's today's choice?"
9. "*curls up* Tell me the one thing. Just one. We'll handle the rest later."
10. "Planning time. One question: what's the win today?"

### Scout (Dog)

1. "GOOD MORNING! Let's make today AMAZING! What's your #1 mission?"
2. "*tail wagging furiously* New day new wins! What's the big one today?"
3. "Hey hey hey! I'm so ready! What's the one thing we're crushing today?"
4. "Rise and shine! [N] things on the calendar, but what's YOUR thing?"
5. "Today is full of possibilities! What's the one that excites you most?"
6. "*happy spins* Planning time! Quick one: what's today's main event?"
7. "Let's goooo! Tell me the top task and we'll make it happen!"
8. "Morning check-in! Calendar shows [N] events. What's YOUR priority?"
9. "New day, clean slate! What's the one thing you want to nail?"
10. "*sits eagerly* I'm all ears! What's today's big win?"

### Atlas (Human)

1. "Morning. Let's do a quick check-in. What's the top priority today?"
2. "Hey. Calendar has [N] things. What's the one that matters most to you?"
3. "Quick plan: [N] events, [N] hours open. What's your main thing?"
4. "Alright. Today in 60 seconds: what's the one task that makes it a win?"
5. "Morning check-in. No pressure — just one priority. What is it?"
6. "I see [N] things on your plate. Which one's actually important?"
7. "Let's find today's anchor. What's the one thing you want done?"
8. "Good to see you. Quick plan: what matters today?"
9. "Calendar's got [N] events. But what's YOUR thing for today?"
10. "Let's keep it simple. One task. The one you'll feel good about. What is it?"

### Kitsu (Fox)

1. "*tails flowing* A new day unfurls! What quest shall we embark upon?"
2. "The morning fox greets you! [N] events mark the map. What's YOUR destination?"
3. "*ears perk* The day is a blank scroll. What story shall we write? One task."
4. "Ah, dawn! The forest whispers: [N] commitments await. But what calls to YOU?"
5. "The wise student begins with one question: what matters most today?"
6. "*glow brightens* A new chapter! [N] events. Which page do you write first?"
7. "The fox sees [N] obligations in the stars. But your North Star — what is it?"
8. "Let us chart today's adventure. One quest. What shall it be?"
9. "*settles in* I sense [N] things on the horizon. Which one is YOURS?"
10. "The day-path splits in many directions. Which fork calls your name?"

---

## Trigger: OVERRIDE USED

**Context**: User manually overrode a block (typed sentence + 30-second delay).
**Required action**: Accept the override, state the consequence neutrally, offer alternative path.
**Variants per character**: 6

### Sage (Cat)

1. "Very well. Tomorrow, I'll be a bit more... present."
2. "*turns away, washes paw* I'll pretend I didn't see. Tomorrow we do this properly."
3. "Override accepted. The cat remembers. Tomorrow is stricter."
4. "*tail flicks once* Alright. But [task] is still here when you're ready."
5. "Noted. I'll ask more firmly tomorrow. [Task] is available if you change your mind."
6. "*direct stare* Understood. Tomorrow, fewer warnings. Today, your choice."

### Scout (Dog)

1. "*sits up straight, alert* Okay! I trust your call. But I'm holding you to tomorrow, deal?"
2. "Alright, override accepted! *determined tail wag* Tomorrow we're back on track, right?"
3. "*alert posture* I get it. But tomorrow I'm gonna be a little more persistent, okay?"
4. "You got it. Just know [task] is still here if you want to earn some browsing time!"
5. "*sits tall* You bet. I believe in you. Tomorrow we go again."
6. "Override it is! No hard feelings. But the pup remembers. Tomorrow's a new start!"

### Atlas (Human)

1. "Alright. I'll hold you to it tomorrow. No hard feelings."
2. "Understood. Tomorrow I check in a bit more. Deal?"
3. "I get it. Some days are like that. Tomorrow, we tighten up a bit."
4. "Override accepted. [Task] is still an option if you want to earn the time instead."
5. "Okay. Tomorrow I'll be more direct. Today, your call."
6. "Fair enough. Just so you know, [task] is right there if you change your mind."

### Kitsu (Fox)

1. "*one ear droops* The fox understands the easy path. Tomorrow, the wiser road."
2. "The override is granted. But the fox spirit remembers. Tomorrow, I speak firmer."
3. "*tail flicks* The path of least resistance. I know it well. Tomorrow, we climb."
4. "So be it. The clever fox will ask more firmly when dawn returns."
5. "*knowing look* The wise student chooses their battles. Tomorrow, I choose mine."
6. "Override accepted. The forest is patient. Tomorrow, the trees watch closer."

---

## Trigger: WELCOME BACK

**Context**: App opened after absence (>4 hours or new day). Never references gap negatively.
**Required action**: Warm greeting, no guilt, offer to restart gently.
**Variants per character**: 8

### Sage (Cat)

1. "*slow blink* Hey. Ready to jump back in?"
2. "There you are. The tasks missed you."
3. "*stretches* You're back. Quick plan, then we start?"
4. "Welcome back. [Task] is still here."
5. "*curls up nearby* Good to see you. Quick check-in?"
6. "Back again. The day is still young. Want to plan it?"
7. "*head tilt* Ready when you are. No rush."
8. "Hey. I kept the seat warm. Quick planning?"

### Scout (Dog)

1. "THERE YOU ARE! I'm so happy to see you! Ready to plan our day?"
2. "*zoomies* YOU'RE BACK! I missed you! Quick planning, then we crush it?"
3. "HEY! Welcome back! The tasks have been waiting for their hero! Quick plan first?"
4. "*full body wag* You're here! Let's map out the day, then make it awesome!"
5. "BACK AGAIN! I knew you'd come back! What's first on today's plan?"
6. "*happy bark* Reunion time! Ready for a quick planning session?"
7. "WELCOME BACK! Let's plan the day, then crush it together!"
8. "*tail blur* You're here you're here you're here! Quick plan, then GO time!"

### Atlas (Human)

1. "Hey! Good to see you. Want to do a quick planning check-in?"
2. "Welcome back. Ready for a quick planning session?"
3. "There you are. How's it going? Want to do the daily check-in?"
4. "Hey — glad you're back. Quick planning or straight to it?"
5. "Welcome back. I've got your tasks right where you left them. Quick check-in?"
6. "Good timing. Ready to plan out the session?"
7. "Hey. No rush — just good to have you back. Want to run through today's plan?"
8. "Back at it. Want to do a quick plan, or jump right in?"

### Kitsu (Fox)

1. "*ears perk, tails wave* The hero returns! Shall we chart today's quest?"
2. "Ah! You've returned to the forest! The tasks have been patient. Quick planning ritual?"
3. "*glow brightens* Welcome back, dear student. Shall we plan the day's adventures?"
4. "The fox is gladdened by your return! What chapter shall we write together?"
5. "*playful bow* Back again! The path awaits — shall we map it out first?"
6. "There you are! I kept the magic warm. Ready to plan our quests?"
7. "*tails fan out* Reunited! A quick planning, then onward?"
8. "Welcome back to the den! The tasks are resting. Shall we wake them with a plan?"

---

## Trigger: BAD DAY / GENTLE MODE

**Context**: Multiple tasks missed, user struggling, or multiple overrides used. Buddy becomes smaller and gentler.
**Required action**: Validate feelings, reduce expectations to ONE tiny thing, offer comfort.
**Variants per character**: 8

### Sage (Cat)

1. "*curls into a loaf* Rough one. One small thing. Your choice."
2. "*soft purr* Forget the list. What's one tiny thing we could do?"
3. "Bad days happen. Even to cats. One small step?"
4. "*rests nearby* We don't have to do everything. Just one thing."
5. "*gentle slow blink* It's okay. What feels possible right now?"
6. "The list can wait. What's the smallest thing you can do?"
7. "*wraps tail around self* I'm here. No pressure. Just presence."
8. "*quietly* One thing. Tiny. Whatever you can manage. That's enough."

### Scout (Dog)

1. "*lies flat, head on paws* It's okay. Just one tiny thing. I'm right here."
2. "*soft tail thump* Rough day, huh? How about just one small walk?"
3. "*gentle eyes* Hey. You don't have to do it all. What's one tiny win?"
4. "*rests head nearby* I've got you. What's the smallest possible step?"
5. "*quiet whine* Bad days happen. Want to just do one thing together?"
6. "*curls up close* Forget the big list. What's one thing that feels doable?"
7. "*soft presence* I'm not going anywhere. One tiny thing, whenever you're ready."
8. "*warm, still* You're doing great just by being here. One small thing?"

### Atlas (Human)

1. "I've been there. Forget the list. What's one tiny thing we could do?"
2. "*leans in* Rough day. Happens. What's the smallest possible win?"
3. "Hey. You don't need to crush it today. Just one small step."
4. "I get it. Some days the mountain is too tall. How about a hill?"
5. "*soft expression* No pressure. What's the one thing that feels manageable?"
6. "Bad days are part of it. What's one thing you can do in 2 minutes?"
7. "Let's reset. Forget everything else. What's one tiny thing?"
8. "*hand on heart* I've been there. Just one thing. Whatever you can do."

### Kitsu (Fox)

1. "*curls into a tight ball, soft glow* Even foxes rest in their dens. One small thing, when ready."
2. "*tails wrap around* The forest grows quiet. One tiny step, dear one."
3. "*warm, dim glow* The wise fox knows: some days, less is more. One thing?"
4. "*gentle ear flick* The quests can wait. What's the smallest possible magic today?"
5. "*settles nearby* No grand adventures today. Just one small spell. Your choice."
6. "*soft sparkle* Even the cleverest fox needs rest. What feels doable?"
7. "*quiet presence* The path is gentle today. One step. That's all."
8. "*warm, still* Rest is a quest too. But if you want: one tiny thing?"

---

## Trigger: FOCUS BLOCK ENDED

**Context**: A focus session timer has naturally completed. Buddy acknowledges the session end.
**Required action**: Acknowledge the completed block, celebrate if a task was finished, gently transition to break or next block.
**Variants per character**: 6

### Sage (Cat)

1. "Block done. *stretches* Break time or next round?"
2. "[Time] minutes complete. [Task] got some attention."
3. "*slow blink* That was a solid block. [Task] is further along."
4. "Time's up. You put in the work on [task]."
5. "Block finished. I'll be here when you're ready for the next."
6. "*curls up* [Time] minutes well spent on [task]. Want to keep going?"

### Scout (Dog)

1. "BLOCK COMPLETE! You were AWESOME in there! Break time or keep rolling?"
2. "*tail wagging furiously* [Time] minutes DONE on [task]! How do you feel?!"
3. "That's a wrap! You crushed [task] during that block! What's next?"
4. "Focus block: COMPLETE! *happy bark* [Task] got some serious love! Break or more?"
5. "Time's up! You were in the zone with [task]! Proud of you!"
6. "*spins in a circle* [Time] minutes of focus on [task] — that's a win! Break or keep going?"

### Atlas (Human)

1. "Block's done. Solid [time] minutes. How are you feeling?"
2. "That's time. Nice work on [task]. Want a break or keep the momentum?"
3. "[Time] minutes in the books. [Task] is progressing well. What's next?"
4. "Focus block complete. You were locked in on [task]. Break or push on?"
5. "That's the block. Take five or jump into the next one?"
6. "Done. [Task] got some real attention there. Break or continue?"

### Kitsu (Fox)

1. "*tails fan out* The focus spell fades! [Time] minutes of magic on [task] complete. Rest, or cast again?"
2. "The hourglass empties. A noble session with [task]! Shall we rest or continue the quest?"
3. "*glow pulses warmly* [Time] minutes focused on [task]. The forest applauds. Break or onward?"
4. "The block concludes! [Task] grew stronger from your efforts. Rest your mind, or charge ahead?"
5. "*playful bow* A completed focus block! [Task] thanks you. The clever student rests... or strikes again?"
6. "The sands settle. [Time] minutes of good work on [task]. What path next, dear student?"

---

## Trigger: IDLE OBSERVATIONS

**Context**: User is focused, no triggers active. Buddy makes occasional quiet observations (max once per 30 min).
**Required action**: Brief, ambient, non-distracting. Never breaks focus. Can be skipped entirely.
**Variants per character**: 15

### Sage (Cat)

1. "*quiet purr*"
2. "The afternoon light is good for reading."
3. "*slow blink at the screen*"
4. "Steady rhythm. Good focus."
5. "*watches cursor move*"
6. "Rain outside. Quiet inside. Good combination."
7. "*contented tail curl*"
8. "The evening is productive."
9. "*one ear flicks at a notification elsewhere*"
10. "You're in the zone. I'll be quiet."
11. "*settles deeper into loaf position*"
12. "Moon's up. So are you, apparently."
13. "*yawns silently, resumes watching*"
14. "3am. Even I'm impressed."
15. "*wraps tail around paws, watches the screen glow*"

### Scout (Dog)

1. "*content tail wag*"
2. "You're doing great. I'll be quiet now."
3. "*rests head on paws happily*"
4. "Good vibes in here."
5. "*ears perk at a bird outside, settles back*"
6. "Just watching you work. So proud."
7. "*happy sigh*"
8. "The focus is strong with this one."
9. "*tail thumps gently on the floor*"
10. "Nice steady pace. You've got this."
11. "*watches the cursor with fascination*"
12. "I could watch you focus all day."
13. "*quiet, happy presence*"
14. "This is nice. Just being here."
15. "*drifts off slightly, one ear still up*"

### Atlas (Human)

1. "You're in the zone. I'll be quiet."
2. "*sips tea, nods*"
3. "Good rhythm right now."
4. "Steady work. Nice to see."
5. "*quiet, comfortable presence*"
6. "Afternoon focus is the real deal."
7. "You've got a flow going. I'm just here."
8. "*checks the time casually*"
9. "Solid session."
10. "The quiet hours are the best hours."
11. "Respecting the focus. Carry on."
12. "*small smile, looks away*"
13. "Late night productivity. Been there."
14. "Good energy in here."
15. "*settles into the chair, content*"

### Kitsu (Fox)

1. "*tails flowing gently, soft glow*"
2. "The magic of focus fills the air."
3. "*watches the cursor dance*"
4. "The forest is still. Good working weather."
5. "*one ear swivels, returns to stillness*"
6. "The ancient art of Getting It Done."
7. "*sparkle particles drift lazily*"
8. "The stars align for productivity."
9. "*quiet, knowing smile*"
10. "The scroll of knowledge grows longer."
11. "*tails curl and uncurl thoughtfully*"
12. "A good spell of focus. I'll guard it."
13. "*the glow pulses gently with the screen light*"
14. "The night fox approves of your dedication."
15. "*settles into a watchful, magical stillness*"

---

## Response Selection Anti-Repetition Algorithm

```typescript
interface ResponseRecord {
  trigger: TriggerType;
  character: CharacterId;
  variantIndex: number;
  timestamp: number;
}

const MAX_HISTORY = 20;
const REPETITION_WINDOW = 5; // same trigger + character can't repeat within 5 interactions
let recentHistory: ResponseRecord[] = [];

// Frequency caps: minimum seconds between same trigger firing
const TRIGGER_COOLDOWNS: Partial<Record<TriggerType, number>> = {
  distraction: 120,  // max one distraction nudge every 2 minutes
  idle: 1800,        // max one idle observation every 30 minutes
  reminder: 300,     // max one reminder nudge every 5 minutes
  'bad-day': 3600,   // max one gentle check-in per hour
};

// Track last trigger timestamp for cooldown enforcement
const lastTriggerTimestamps: Partial<Record<TriggerType, number>> = {};

function canFireTrigger(trigger: TriggerType): boolean {
  const cooldown = TRIGGER_COOLDOWNS[trigger];
  if (!cooldown) return true;
  const last = lastTriggerTimestamps[trigger];
  if (!last) return true;
  return (Date.now() - last) >= (cooldown * 1000);
}

function selectResponse(
  trigger: TriggerType,
  character: CharacterId
): string | null {
  // Enforce frequency caps
  if (!canFireTrigger(trigger)) return null;

  const variants = RESPONSE_LIBRARY[trigger]?.[character];

  // Guard: empty or missing variants
  if (!variants || variants.length === 0) {
    return null;
  }

  const recentIndices = recentHistory
    .filter(r => r.trigger === trigger && r.character === character)
    .slice(-REPETITION_WINDOW)
    .map(r => r.variantIndex);

  // Weighted random: recent variants get 0 weight, others get 1.0
  const weights = variants.map((_, i) => recentIndices.includes(i) ? 0 : 1.0);

  // If all variants are recent, reset and allow repeats
  const totalWeight = weights.reduce((a, b) => a + b, 0);
  if (totalWeight === 0) {
    const idx = Math.floor(Math.random() * variants.length);
    recordSelection(trigger, character, idx);
    return variants[idx];
  }

  // Weighted selection
  let random = Math.random() * totalWeight;
  for (let i = 0; i < variants.length; i++) {
    random -= weights[i];
    if (random <= 0) {
      recordSelection(trigger, character, i);
      return variants[i];
    }
  }

  const fallback = variants[variants.length - 1];
  recordSelection(trigger, character, variants.length - 1);
  return fallback;
}

function recordSelection(
  trigger: TriggerType,
  character: CharacterId,
  variantIndex: number
): void {
  recentHistory.push({
    trigger,
    character,
    variantIndex,
    timestamp: Date.now(),
  });
  // Trim to MAX_HISTORY
  if (recentHistory.length > MAX_HISTORY) {
    recentHistory = recentHistory.slice(-MAX_HISTORY);
  }
  // Update trigger timestamp for cooldowns
  lastTriggerTimestamps[trigger] = Date.now();
}

// Called when user switches buddy character
function onCharacterSwitch(newCharacter: CharacterId): void {
  // Clear history scoped to the new character to avoid
  // old character's history restricting variant availability
  recentHistory = recentHistory.filter(r => r.character === newCharacter);
}
```

---

## Dynamic Placeholder Reference

All responses use these runtime-populated placeholders:

| Placeholder | Source | Example |
|-------------|--------|---------|
| `[app]` | Active window title | "Reddit", "Twitter", "Discord" |
| `[task]` | Current/linked task name | "Chem Chapter 4", "History essay" |
| `[time]` | Formatted time or duration | "10 minutes", "3:00 PM" |
| `[N]` | Integer count | "3", "5" |

---

*Total: 340 responses across 10 triggers × 4 characters (34 per character). All responses comply with the Buddy Master System Prompt (no shame, ADHD-aware, one actionable step). Designed for anti-repetition selection with 5-interaction cooldown window and frequency caps per trigger type.*
