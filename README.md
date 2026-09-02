# ClickTrack

A dead-simple tap-to-count app. No menus, no accounts — just named buttons you hit to accumulate a number, with a rest timer always within reach.

Live at: https://lancelot2112.github.io/clicktrack/

Built as a single `index.html` — no build step, no dependencies, no backend. Open it and it works.

## The idea

Name an accumulator ("Push-ups", "Bets won", "Jinxes"), then hit its button to add to it. Useful for workouts, where digging through app menus mid-set is miserable, and equally good for frivolous pursuits like bet tracking or jinx tallies.

## Requirements / features

### Main screen
- Grid of compact tiles, ~4 across on a phone, styled as glossy pressable buttons in per-counter colors
- Tiles can be organized into named **groups** (e.g. *Workout* vs *Games*), rendered as sections
- **Tap a tile** = instantly add that counter's configured tap amount (the number bumps in place)
- **Hold a tile** (~half a second, with a haptic tick) = open the counter's detail screen
- A badge in each tile's lower-right corner shows what a tap does (`+1`, `+5`, `−5`, ...)
- Each tile displays a configurable stat: **today**, **this month**, or **lifetime** (a push-up tile might show today; a jinx tile, lifetime)
- A **global default timer** is pinned to the bottom of the main screen (0:30 / 1:00 / 1:30 presets)

### Counter detail screen
- Big "today" number, plus this-month and lifetime stats
- Editable **quick-add preset buttons** (e.g. +1, +5, +10 — decimals and negatives allowed)
- Free-form amount field for one-off adds
- **Undo** for the last add
- **Timer pinned at the bottom** with per-counter preset times, start/pause, reset, a progress bar, and an audible beep (plus vibration) when it hits zero
- Counters can opt out of the timer entirely (leave timer presets blank and the bar disappears)

### Per-counter settings
- Name, group, unit label (reps, $, jinxes...)
- Tap amount for the main-screen tile (negative = decrement)
- Quick-add preset amounts
- Timer preset times (seconds or `m:ss`), or none
- Which stat the tile displays (today / month / lifetime)
- Color

### Data
- Everything stays on-device in the browser's `localStorage` — no server, no account
- Daily totals are kept per-day so today/month/lifetime stats roll up automatically (history pruned past ~400 days)
- Saves are debounced and retried; if storage is unavailable the app keeps working in-memory and says so

## Using it on a phone

Open the GitHub Pages URL and use **Add to Home Screen** (Share menu on iOS, browser menu on Android). It opens full-screen like a native app.

Note: data lives in that device's browser storage. Clearing site data wipes it, and counts don't sync between devices.

## Ideas not yet built

- Undo toast on the main screen after a tap
- Custom ordering of groups/tiles (currently alphabetical)
- Daily history view / charts
- Export & backup
- Sync across devices
