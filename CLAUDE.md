# Workout Tracker

## What this is
A personal workout tracker for my own use. Single user (just me), used mainly
on my iPhone in the browser. Not a product — simplicity beats features.

## Tech & constraints
- Everything lives in a single `index.html` file (HTML, CSS, and JS all
  embedded). No build step, no separate files, no frameworks or dependencies.
- Data is stored locally in the browser using **localStorage** (key:
  `workouts_v1`). Nothing is sent to a server. Keep it that way unless I
  explicitly ask for sync.
- Must work well on a phone screen first. Test with a narrow viewport.

## Data model
Each workout entry is a flat object stored in a JSON array:

```
id, date, exercise, sets, reps, weight, tempo, comment, unit,
superset, exercise2, sets2, reps2, weight2, tempo2, comment2
```

- `tempo` format: `#.#.#.#` (e.g. `3.0.0.1` = eccentric · pause · concentric · pause)
- `unit`: `'lbs'` or `'kg'` — chosen per entry via a segmented picker; weight is stored as-is with no conversion. Defaults to `'lbs'` for old entries missing this field.
- `superset: true` means the entry has a second exercise (exercise2 and its fields)
- Fields are empty strings `""` when not filled in, never `null`

## UI patterns (follow these for new features)
- Toggle switches for optional fields (tempo, superset already use this)
- Card-based layout with 14px border-radius, soft shadow
- iOS-style colors: `#007aff` blue, `#f2f2f7` background, `#1c1c1e` text
- Buttons minimum 44px tall for comfortable touch targets
- Past workouts are grouped by day, collapsed by default, tap to expand

## Form behaviour
- After saving, the date field stays filled (convenient for logging multiple
  exercises in one session). All other fields clear.
- Tempo and superset sections are hidden by default behind toggles.

## Design principles
- Mobile-first, minimal, large tap targets.
- Logging a workout should be fast and require as few taps as possible.
- Don't add features not explicitly requested.

## Deployment
- Hosted on GitHub Pages at **https://ottyem.github.io/workout-tracker**
- After committing, run `git push` to publish. GitHub Pages rebuilds in ~60 seconds.

## How I like to work
- I'm rusty at coding, so explain changes briefly and avoid unexplained jargon.
- Make one change at a time so I can check each result.
- Commit to git each time something works.
- Ask before any big refactor or structural change.
