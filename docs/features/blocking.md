# System-Wide Blocking — Feature Specification

## Overview

FocusPath blocks distracting websites and applications system-wide using OS-level mechanisms (hosts-file manipulation on Mac, equivalent on Windows). The key differentiator: blocking is never a hard wall — it uses escalating friction with a deliberate unlock path, and gates access on task completion, not time elapsed.

## Design Rationale

Research and community feedback identifies three critical failures in existing blockers:

1. **Hard blocks cause panic** — being fully locked out triggers anxiety and uninstalls
2. **Workaround syndrome** — if the wall can be bypassed, trust in the tool collapses
3. **Time-based gating fails** — ADHD time blindness means "25 minutes" is meaningless

FocusPath solves all three: escalating friction (never a hard wall), task-gated unlock (meaningful milestone, not a timer), and buddy accountability (bypassing has social/emotional cost with the buddy).

## Escalating Friction Model

### Level 1: Gentle Nudge
- **Trigger**: First visit to distracting site/app in a focus session
- **Response**: Buddy speech bubble: "Hey, you're in a focus block. Still want to browse Reddit?"
- **Action required**: Click "I'll stay focused" or "Just 5 minutes"
- **If ignored**: Bubble persists, buddy expression shifts to concerned

### Level 2: Active Warning
- **Trigger**: Second distraction in same session, or >5 minutes on a distracting site
- **Response**: Site/app overlay with buddy message: "You've been here 5 minutes. Chem chapter is waiting."
- **Action required**: Button click to dismiss + confirm intention
- **Duration**: Overlay stays for 10 seconds, cannot be dismissed immediately

### Level 3: Soft Lock + Deliberate Unlock
- **Trigger**: Third+ distraction, or exceeding daily leisure budget
- **Response**: Full-screen overlay: "This site is locked during focus hours."
- **Action required**: Typed-sentence commitment ("I will return to my tasks") + 30-second countdown timer
- **During countdown**: Buddy reminds user of pending tasks

### Level 4: Task-Gated Lock
- **Trigger**: Daily leisure budget exhausted, and tasks remain incomplete
- **Response**: "Complete 1 task to unlock 30 minutes of browsing."
- **Action required**: Mark a task as done in the buddy panel
- **No bypass**: The typed-sentence override is NOT available at this level — only task completion

### Manual Override (Always Available)
- Available at Levels 1-3, not Level 4
- Requires: typed commitment sentence + 30-second delay
- **Consequence**: Buddy becomes stricter tomorrow (more confirmation steps, less generous time budgets)
- This prevents the "panic trap" while maintaining long-term effectiveness

## Task-Gating System

### Daily Budget Model
- User sets daily leisure time budget (default: 60 minutes)
- Budget can be split across sites/apps or shared pool
- Budget consumed by active time on blocked sites

### Task Unlock Tiers
| Tasks Completed | Unlock |
|----------------|--------|
| 1 task | +30 minutes leisure |
| 2 tasks | +30 more minutes (60 total) |
| 3+ tasks | Unlimited leisure for rest of day |
| All daily tasks | Full unlock + buddy celebration |

### Configurable Threshold
- User sets minimum tasks per day (e.g., "3 of 5 tasks = free browsing")
- Can adjust per day — flexible, not rigid

## User Configuration

### Block Lists
- **Sites**: Domain-based blocking (reddit.com, twitter.com, youtube.com)
- **Apps**: Process-name-based blocking (Discord.exe, Slack.exe)
- **Categories**: Pre-built lists (Social Media, News, Gaming, Streaming)
- **Custom**: User-defined additions and exceptions

### Schedules
- **Focus hours**: Recurring blocks (Mon-Fri 9am-5pm)
- **One-off sessions**: "Block for the next 2 hours"
- **Task-linked**: Block only while specific tasks are incomplete
- **Always-on optional**: Manual activation for unscheduled focus

### Site/App Classification
- User marks each detected app as: Productive / Neutral / Distracting
- Pre-built classifications for common apps
- Buddy only blocks "Distracting" apps
- "Neutral" apps are tracked but not blocked
- "Productive" apps contribute to focus statistics

## Technical Approach

### Mac: Hosts-File Manipulation
```
1. App requests admin privileges (explained in onboarding)
2. Backup original hosts file to ~/Library/Application Support/FocusPath/
3. Append blocked domains → 127.0.0.1
4. Flush DNS cache: sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
5. On app close/disable: restore original hosts file
6. On crash: watchdog process restores hosts file
```

### Windows: Hosts-File + (potential) Windows Filtering Platform
```
1. App requests admin privileges (explained in onboarding)
2. Modify C:\Windows\System32\drivers\etc\hosts (with backup)
3. Flush DNS: ipconfig /flushdns
4. Alternative/advanced: Windows Filtering Platform API for per-process blocking
```

### Cross-Platform Abstraction
```typescript
interface BlockerBackend {
  block(domains: string[]): Promise<void>;
  unblock(domains?: string[]): Promise<void>;
  unblockAll(): Promise<void>;
  isBlocked(domain: string): Promise<boolean>;
  backupHosts(): Promise<void>;
  restoreHosts(): Promise<void>;
}
```

## Safety Mechanisms

- **Crash recovery**: Watchdog process that restores hosts file if main process dies unexpectedly
- **Auto-unblock**: All blocks lift when app is properly closed
- **Emergency unblock**: User can always quit FocusPath from system tray to restore access
- **Backup always exists**: Original hosts file saved before any modification
- **Clear status indicator**: System tray icon shows blocking status (active/inactive)

## Onboarding (Permission Flow)

1. **Education card**: "FocusPath needs to modify your computer's hosts file to block distracting sites. Here's exactly what that means..."
2. **Technical explanation**: Plain-language description of hosts-file blocking
3. **Safety promises**: "You can quit FocusPath anytime to restore access. We never block essential system domains."
4. **OS permission prompt**: Standard admin password prompt
5. **Confirmation**: "All set! FocusPath will only block sites when you tell it to."

## Privacy

- Block/unblock events logged locally only
- No browsing data collected
- No URLs visited — only domain-level blocking
- All configuration stored in local SQLite

## v1 MVP Scope

- [ ] Hosts-file blocking on ONE platform (prioritize development OS)
- [ ] Three friction levels (nudge, warning, typed-sentence)
- [ ] Basic task-gating (complete 1 task = unlock)
- [ ] Manual override with 30-second delay
- [ ] Pre-built block lists (Social Media, Gaming, Streaming)
- [ ] Onboarding permission explanation flow
- [ ] System tray status indicator
- [ ] Crash recovery watchdog

## v2 Enhancements

- [ ] Cross-platform (both Mac and Windows)
- [ ] Full escalating friction model (4 levels)
- [ ] Task unlock tiers (1 task = 30min, 2 = 60min, all = unlimited)
- [ ] Stricter-after-override calibration
- [ ] Per-app blocking (not just hosts-file)
- [ ] Windows Filtering Platform integration
- [ ] Custom block schedules
