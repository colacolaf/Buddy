# Fullscreen Layout Styles

A FocusPath fullscreen module is any primary section that takes over the whole app window. These are the four layout styles used across the app.

## 1. Tabbed Container
One row of tabs, one scrollable content pane.
- **Best for:** Settings, Blocking, complex configuration
- **Pros:** Fast section switching; familiar; compact header
- **Cons:** Hides everything except the active tab
- **Example:** Blocking v1 (Status / Lists / Schedule / Settings)

## 2. Single-Scroll Stack
All sections stacked vertically on one long page.
- **Best for:** Status dashboards, Done List, Stats, read-heavy flows
- **Pros:** No navigation decisions; everything is one scroll away
- **Cons:** Can get long; needs strong section hierarchy
- **Example:** Blocking v2, Done List

## 3. Split Panes
A pinned left pane (status/hero) + a scrollable right pane (details/config).
- **Best for:** Focus session, Planning ritual, Goals
- **Pros:** Context always visible; clear primary/secondary separation
- **Cons:** Narrow on small screens; left pane can feel empty
- **Example:** Blocking v3

## 4. Three-Column Command Center
Sidebar + main content + detail panel.
- **Best for:** Calendar, complex planning, AI-assisted scheduling
- **Pros:** Maximum information density; detail stays visible on selection
- **Cons:** Heavy cognitive load; needs generous whitespace
- **Example:** Calendar (detail left, month center, AI sidebar right)

---

## Choosing a Style

| Module | Recommended style | Why |
|---|---|---|
| Calendar | Three-Column Command Center | Needs month grid + selected day + AI chat |
| Blocking | Tabbed or Split Panes | Status + settings are two distinct mental modes |
| Goals | Split Panes | Goal tree left, details/editor right |
| Done List | Single-Scroll Stack | One long feed of wins; no tabs needed |
| Stats | Single-Scroll Stack or Tabbed | Charts grouped by time or category |
| Planning Ritual | Split Panes | Buddy prompt left, calendar/task preview right |
| Buddy Chat | Split Panes or Three-Column | Chat center, quick actions right |
| Settings | Tabbed Container | Many unrelated categories |
