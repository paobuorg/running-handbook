---
entityId: tool:race-calendar-planner
locale: en
title: "Race calendar planner — five dated phases around a goal race, next race and recovery"
summary: "Enter today, goal race, distance, weekly volume and next race to get dated base, build, taper, race and recovery phases, plus whether the next race is a race, training or skip."
aliases: ["赛历规划器", "race calendar planner", "赛季规划", "比赛排期"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

The common calendar mistake is squeezing races into the diary without counting the weeks between them. This tool takes today, a goal race, an optional next race and current weekly volume, then returns total weeks, dated base/build/taper/race/recovery phases, the gap to the next race and whether that next race should be a race, training or skipped.

It does not check entry eligibility or whether a time goal is realistic. It makes the time visible before you enter, so you can see whether recovery actually fits.

## Inputs and outputs

Five inputs: today (YYYY-MM-DD), goal race date, goal distance (5k/10k/half/marathon/ultra), current weekly volume (10–300 km) and next race date (optional). Outputs are total weeks, build weeks, taper weeks, recovery days, a phase table, gap days, next-race role and warnings.

“Today” is typed, not read from the device clock, so you can plan from a future date or review a past season.

## Formula and phases

```
totalWeeks = floor((goalDate - today) / 7 days)
buildWeeks = totalWeeks - taperWeeks
baseWeeks = max(1, floor(buildWeeks × 0.5))
peakWeeks = max(1, buildWeeks - baseWeeks)
taperStart = goalDate - taperWeeks × 7
recoveryEnd = goalDate + recoveryDays
```

Taper by distance: 5k/10k 1 week, half 2, marathon/ultra 3. Recovery: 5k 5 days, 10k 7, half 10, marathon 14, ultra 21. Base and peak split the build in half; the taper always ends the day before the race.

## Phase table

| Phase | Start | End | Purpose |
|---|---|---|---|
| Base | today | end of base weeks | aerobic volume, strength |
| Build | next day | before taper | threshold, long runs, race pace |
| Taper | taper start | day before race | cut volume, keep intensity |
| Race | goal date | goal date | execute |
| Recovery | day after | recovery end | walk, walk-run, return |

The dates are a skeleton; weekly volume and intensity need a coach or a training plan.

## Case one: marathon on 2027-04-11

| Item | Result |
|---|---|
| Total weeks | 19 |
| Build weeks | 16 |
| Taper weeks | 3 |
| Recovery days | 14 |
| Base | 2026-11-26 — 2027-01-20 |
| Build | 2027-01-21 — 2027-03-20 |
| Taper | 2027-03-21 — 2027-04-10 |
| Next race 2027-10-10 | 182 days, race |

A classic “19 weeks left” marathon: eight weeks base, eight build, three taper. The next race is half a year away, so recovery fits and it can be an A race.

## Cases two and three

| Scenario | Total | Build | Taper | Recovery | Next race |
|---|---|---|---|---|---|
| 5k on 2027-01-23 | 8 | 7 | 1 | 5 days | not set |
| ultra on 2027-08-27 | 34 | 31 | 3 | 21 days | 09-10, skip |

The 5k has only eight weeks: three base, four build, one taper. That is not permission to cram; it is the reality of the time available. The ultra followed by another race 14 days later is judged skip, because 21 days recovery plus a 7-day buffer do not fit.

## Next-race role

| Gap | Role | Meaning |
|---|---|---|
| under recovery+7 days | skip | not recovered; entry is pointless |
| recovery+7 to +21 days | training | run it, do not chase a time |
| over recovery+21 days | race | a target is allowed |

This rule handles time only, not eligibility, travel, money or family. It is not a medical judgement; after injury or illness, count recovery separately.

## Boundaries

The tool assumes a fixed goal date, a healthy runner, no injury and no long-haul travel. If a date may move with a lottery or entry window, draft with the expected date and recalculate after confirmation.

A build under six weeks is flagged as “completion, not peak”; that is not a demand to withdraw, but a change from PB to safe finish. Under four weeks the tool returns an error.

## Chinese runners and the 2027 calendar

Chinese race dates are often published three to six months out, and many 2027 events remain TBD. Draft with known dates, keep TBD events in a candidate column, and do not lock a season to an unpublished date.

For overseas goals, put visa, flights, jet lag and qualification windows in the same table; this tool only builds training phases. Use the [race travel planner](/en/tools/race-travel-planner/) for the trip.

## Common mistakes

One: treating total weeks as training weeks and forgetting the taper. Two: counting recovery as zero and starting a new plan the day after the race. Three: setting a PB target with four weeks between races. Four: planning precisely around an unpublished date.

Five: scheduling only the A race, no B/C races. Six: running a “training” race all out. Seven: calculating recovery after entering instead of before.

## Checklist

Before input: confirm today, goal date, distance, current volume and next date. After output: put the five phases in the calendar; confirm the next-race role; check whether the build is under six weeks; check whether the goal date is officially published.

If a date comes from a lottery or entry window, verify it on the route page first, then recalculate.

## Related reading and tools

Read the [2027 calendar](/en/calendar/) for published dates; read [entry and calendar strategy](/en/knowledge/race-calendar-entry-strategy/) for windows and budgets; use the [recovery planner](/en/tools/recovery-planner/) to fill recovery; use the [taper planner](/en/tools/taper-planner/) for the last 2–3 weeks.

Route pages mark whether a 2027 date is official or TBD; do not build a hard plan on a TBD date.

- [Race checklist: generated by surface, duration and weather](/en/tools/race-checklist/)

## Lotteries and entry windows

For lottery races, put three dates next to the phase table: entry opens, entry closes, result date. The tool builds training phases; it cannot remember windows for you. Set a reminder two weeks before entry closes.

If the result arrives only four to six months before the race, prepare a “in” and “not in” plan: on the not-in version, turn race day into a training race or long run instead of waiting. UTMB, Western States and Boston windows differ substantially; verify on the route page before planning.

## Why recovery cannot be zero

Starting a new plan the day after the race folds recovery into the build: the first two “easy” weeks become hidden load, and week-three quality lands on unrepaired tendon. Fourteen days for a marathon and 21 for an ultra are floors, not suggestions.

When the next race is too close, “skip” is not conservatism; it prices the entry fee, travel and injury risk into the time account. Moving the next race beyond recovery+21 days is usually cheaper than forcing it.

## Sources and verification boundary

The taper and recovery ranges draw on public Boston, UTMB and Western States calendars and qualification pages, plus general periodisation practice; sources and claims are in the entity JSON. It is not a coaching plan and does not replace official race dates.

Last verified: 2026-11-26. Next review trigger: 2027 calendar updates, taper/recovery range changes, entry-window changes.
