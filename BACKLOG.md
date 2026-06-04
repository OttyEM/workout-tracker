# Backlog

## Phase 1 — Quick wins (low effort, no architectural change)
- ~~Autocomplete movement names from movements already in the database when logging.~~
- ~~Export a single day's data (alongside the existing full export).~~
- ~~Deploy the app online so I can reach it from my phone on any network
  (data still stored locally on-device for now).~~

## Phase 2 — Movement-centric structure
- Left-hand navigation menu with two sections: "Workout" and "Movement list".
- Movement list page showing every movement I've used.
- Auto-calculate RMs (1RM, 3RM, 5RM, 10RM) from logged sets, with the
  option to enter an RM manually instead.
- Movement detail page: open a movement to see its RMs and the full
  history of every time it was done, with sets and reps.

## Phase 3 — Online database (cross-device access)
- Move data to an online database so the same data is available on both
  laptop and phone.

## Phase 4 — Advanced / AI / long term
- Auto-parse a photo of my week's workouts and file each entry into the
  correct day.
- Upload videos when entering an exercise (long term).

## Done
- v1: log entries (date, exercise, sets, reps, weight), view history,
  edit/delete, JSON export.
- Autocomplete exercise names from existing history (custom dropdown, iOS Safari compatible).
- Single-day share as print-to-PDF (opens formatted print page, saves to Files or shares via AirDrop/Mail on iPhone).
- Deployed on GitHub Pages at https://ottyem.github.io/workout-tracker
