# Program Import Format

Import a training program via **Workout → Import Program** (the toolbar button).
The file must be a `.json` file with the structure below.

---

## Top-level structure

```json
{
  "days": [ ...day objects... ]
}
```

---

## Day object

```json
{
  "date": "2026-06-30",
  "exercises": [ ...exercise objects... ]
}
```

| Field       | Required | Description                        |
|-------------|----------|------------------------------------|
| `date`      | yes      | ISO date `YYYY-MM-DD`              |
| `exercises` | yes      | Array of exercises for that day    |

---

## Exercise object (standard)

```json
{
  "exercise": "Squat",
  "sets": "4",
  "reps": "5",
  "unit": "lbs",
  "tempo": "3.0.1.0",
  "comment": "Keep chest up"
}
```

| Field      | Required | Description                                              |
|------------|----------|----------------------------------------------------------|
| `exercise` | yes      | Movement name (string)                                   |
| `sets`     | no       | Number of sets (string)                                  |
| `reps`     | no       | Reps — single value `"10"` or per-set `"10,8,9,8"` or time-based `"30sec"` |
| `unit`     | no       | `"lbs"` or `"kg"` — defaults to `"lbs"`                 |
| `tempo`    | no       | Four-part tempo `"eccentric.pause.concentric.pause"` e.g. `"3.0.1.0"` |
| `comment`  | no       | Free-text coaching note shown under the entry            |

Weight is intentionally left blank on import — you fill it in after the session.

---

## Exercise object (superset)

Add `"superset": true` and the Exercise B fields to link two movements.

```json
{
  "exercise": "Pull-up",
  "sets": "3",
  "reps": "8",
  "unit": "lbs",
  "superset": true,
  "exercise2": "Dip",
  "sets2": "3",
  "reps2": "10",
  "unit2": "lbs",
  "comment2": "Lean forward slightly"
}
```

| Field       | Required        | Description                        |
|-------------|-----------------|------------------------------------|
| `superset`  | yes (for B)     | `true` to enable the second exercise |
| `exercise2` | yes (for B)     | Movement name for Exercise B       |
| `sets2`     | no              | Sets for Exercise B                |
| `reps2`     | no              | Reps for Exercise B (same format as `reps`) |
| `unit2`     | no              | `"lbs"` or `"kg"` for Exercise B  |
| `tempo2`    | no              | Tempo for Exercise B               |
| `comment2`  | no              | Note for Exercise B                |

---

## Full example

```json
{
  "days": [
    {
      "date": "2026-06-30",
      "exercises": [
        {
          "exercise": "Squat",
          "sets": "4",
          "reps": "5",
          "unit": "lbs",
          "tempo": "3.0.1.0",
          "comment": "Stop just below parallel"
        },
        {
          "exercise": "Bench Press",
          "sets": "3",
          "reps": "8",
          "unit": "lbs"
        }
      ]
    },
    {
      "date": "2026-07-02",
      "exercises": [
        {
          "exercise": "Deadlift",
          "sets": "1",
          "reps": "5",
          "unit": "kg"
        },
        {
          "exercise": "Pull-up",
          "sets": "3",
          "reps": "8",
          "unit": "lbs",
          "superset": true,
          "exercise2": "Dip",
          "sets2": "3",
          "reps2": "10",
          "unit2": "lbs"
        },
        {
          "exercise": "Plank",
          "sets": "3",
          "reps": "30sec"
        }
      ]
    }
  ]
}
```

---

## Notes

- Exercises appear in the app in the **same order** as in the JSON.
- Multiple days can be imported at once — each day is added independently.
- Importing does **not** overwrite existing entries for those dates; new entries are appended.
- If a date already has entries, the imported exercises appear after them.
