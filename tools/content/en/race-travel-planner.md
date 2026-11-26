---
entityId: tool:race-travel-planner
locale: en
title: "Race travel planner — jet lag, recommended arrival and start in home time"
summary: "Enter home/destination UTC offsets, race and arrival dates and local start time to get offset direction, adaptation days, recommended arrival, start in home time and a daily sleep table."
aliases: ["比赛旅行规划器", "race travel planner", "时差规划", "jet lag planner"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

Two common misreads in overseas racing: treating “arrive two days early” as adaptation, and reading the start time in home time. This tool takes home and destination UTC offsets, race date, arrival date and local start time, then returns the offset, direction, recommended arrival, start in home time, daily shift and a sleep table.

It does time-zone and date arithmetic only; it does not prescribe melatonin, light exposure or medication. Sleep disorders, shift work, travelling with an infant and long connections are outside the model.

## Inputs and outputs

Five inputs: home UTC offset (-12 to +14), destination UTC offset, race date, arrival date and local start time (HH:MM). Outputs are offset, direction (east/west/same), adaptation days needed, recommended arrival, arrival lead, start in home time, daily shift, readiness and a sleep plan.

Offsets are whole hours; half-hour zones such as India +5.5 or Nepal +5.75 are not supported. Round to the nearest hour and note the correction, or adjust manually.

## Formula and rules

```
offset = destinationOffset - homeOffset
direction = east if offset > 0, west if < 0, same if 0
neededDays = 0 (same zone) or ceil(abs(offset) / rate)
rate = 1 h/day east, 1.5 h/day west
recommendedArrival = raceDate - (neededDays + 1)
startHomeClock = startLocal - offset × 60 minutes
shiftPerDay = abs(offset) / neededDays (one decimal)
```

The “+1 day” buffer covers packet pickup, course familiarity and delays, not extra adaptation. When the home-time start crosses midnight it is marked “-1d” or “+1d”.

## Input ranges

| Input | Range | Meaning |
|---|---|---|
| Home offset | -12 to +14 | whole hours |
| Destination offset | -12 to +14 | whole hours |
| Race date | real date | YYYY-MM-DD |
| Arrival date | not after race date | YYYY-MM-DD |
| Start time | 00:00–23:59 | local clock time |

Arrival after the race fails; invalid dates fail as well.

## Case one: Shanghai to Tokyo, 2027-03-07

| Item | Result |
|---|---|
| Offset | +1 h east |
| Adaptation needed | 1 day |
| Recommended arrival | 2027-03-05 |
| Arrival lead | 3 days, ready |
| Start in home time | 08:10 |
| Sleep plan | 21:30 bed, 05:30 wake |

Tokyo is only one hour away, so three days early is generous. The value of the table is the reminder to wake and sleep on local clock time, not to keep Shanghai hours.

## Cases two and three

| Scenario | Offset | Needed | Recommended arrival | Lead | Status |
|---|---|---|---|---|---|
| Shanghai to New York, 2027-11-07 | -13 h west | 9 days | 2027-10-28 | 3 days | very short |
| Shanghai to Shanghai, 2027-04-04 | 0 | 0 | 2027-04-03 | 3 days | ready |

New York is 13 hours west; at 1.5 h/day that is 9 days. Arriving only three days early is flagged very short. A same-zone race needs no adaptation but still benefits from one day early for pickup and transport.

## How to read readiness

| Status | Condition | Suggestion |
|---|---|---|
| Ready | lead ≥ needed+1 days | follow the sleep table |
| Short | lead ≥ needed days | sleep and wake on local time immediately |
| Very short | lead < needed days | change flights or switch the goal to finish |

Status is not a medical judgement. If you already have a sleep disorder, talk to a doctor or sleep specialist whatever the status.

## How to use the sleep plan

The bedtime and wake times are clock targets, not “must lie down” orders. On arrival, anchor the rhythm with local breakfast, lunch and sunset; get daylight, cut evening screens and caffeine. Eastward means advance sleep, westward delay; move no more than the daily step in the table.

Do not force an early night before the race. After a few days, race-eve bedtime should be close to target; if it is far off, protect sleep duration rather than chase a perfect clock time.

## Boundaries

The tool assumes a direct flight or a normal sleep opportunity; it does not handle red-eyes, overnight connections, shift work, infants or sleep apnoea. It also assumes a fixed start time, ignoring waves, delays or weather rescheduling.

Altitude, heat and course difficulty are separate; good jet-lag adaptation does not mean altitude adaptation. For overseas races, put visa, insurance, pickup and transport in the same trip plan.

## Chinese runners

Flying east to Europe (6–7 hours) is usually easier than flying west to the US west coast (15–16 hours); the US east coast at 12–13 hours is the hardest. If budget allows, arrive 4–5 days early eastward and 7–10 days westward rather than “arrive and sleep”.

With only two or three days, switch the goal from PB to safe finish, eat breakfast on local time three hours before the start and fuel with familiar stomach habits. Do not treat unresolved jet lag as a willpower problem.

## Common mistakes

One: treating “two days early” as two days of adaptation without checking the offset. Two: a four-hour nap on arrival afternoon, then no sleep at night. Three: adjusting only on race eve. Four: reading local time only and missing home-time calls or broadcasts.

Five: treating a red-eye as “saving a day”. Six: building a complex plan for a same-zone race. Seven: using caffeine to push through and ignoring total sleep.

## Checklist

Before input: confirm offsets, race date, arrival date and start time. After output: put recommended arrival and the sleep table in the calendar; confirm visa, pickup and transport; check whether the home-time start crosses a day; confirm readiness.

If readiness is very short, change the flight or the goal before changing the sleep table.

## Related reading and tools

Read [jet lag and race travel](/en/knowledge/jet-lag-and-race-travel/) for light and schedule strategy; read [sleep and recovery](/en/knowledge/sleep-recovery/) for pre-race sleep; use the [race calendar planner](/en/tools/race-calendar-planner/) to fit travel into the training phases.

Route pages list start times and pickup information; verify on the official page before returning to the tool.

- [Race checklist: generated by surface, duration and weather](/en/tools/race-checklist/)
- [2027 race calendar and entry strategy: one table for ballots, travel and recovery](/en/knowledge/race-calendar-entry-strategy/)

- [Altitude acclimation planner: arrival and staging schedule by race altitude](/en/tools/altitude-acclimation-planner/)

## Sources and verification boundary

The direction and recommended arrival are arithmetic; the adaptation rates draw on general sleep and travel research. Sources and claims are in the entity JSON. This is not sleep-medicine advice and does not replace airline or visa requirements.

Last verified: 2026-11-26. Next review trigger: time-zone database changes, sleep-guideline updates, race start-time changes.
