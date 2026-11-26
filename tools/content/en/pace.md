---
entityId: tool:pace
locale: en
title: "Pace calculator: distance, time, pace and speed"
summary: "Choose any two of distance, time and pace to solve the third, with pace per kilometre, pace per mile and average speed shown together. A road-running arithmetic tool that does not model hills, stops or wind."
aliases: ["pace calculator", "pace per kilometre", "speed conversion", "pace chart"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

The pace calculator takes any two of distance, time and pace, solves the third, and shows pace per kilometre, pace per mile and average speed together. It is for runners converting a race target, reviewing a completed run, or translating a treadmill speed into an outdoor pace. It handles a constant average only: start corrals, aid-station stops, hills and wind are not modelled. If you need a kilometre-by-kilometre race plan, use the [split table](/en/tools/splits/). If you want to judge training intensity, do not treat a pace number as the conclusion.

## Formula and units

The calculation uses metres and seconds internally and converts units only at the input and output boundaries.

| Mode | Known values | Solved value | Formula |
| --- | --- | --- | --- |
| Distance + time | Distance, total seconds | Pace, speed | Pace per km = total seconds ÷ kilometres |
| Distance + pace | Distance, seconds per pace unit | Total time | Total seconds = pace seconds × distance in metres ÷ metres per pace unit |
| Time + pace | Total seconds, seconds per pace unit | Distance | Distance in metres = total seconds ÷ pace seconds × metres per pace unit |
| Unit conversion | Pace per kilometre | Pace per mile, speed | Pace per mile = pace per km × 1.609344; speed = kilometres ÷ (total seconds ÷ 3600) |

- A pace input means time per kilometre or per mile in the selected unit; changing the unit changes its meaning.
- The result is always an average, never the pace of any single segment.

## Worked example

- 10 km in 3000 seconds: 300 s/km (5:00/km), 482.8032 → 483 s/mi, 12.00 km/h.
- 5 miles in 2400 seconds: 480 s/mi (8:00/mi), 298.258 → 298 s/km, 12.07 km/h.
- 10 km at 300 s/km: total time 3000 seconds and speed 12.00 km/h.
- 2400 seconds at 480 s/mi: 5 miles, or 8.04672 km, at 298 s/km.

These cases are independent arithmetic.

## Rounding and tolerance

Pace is rounded to the nearest whole second per kilometre or mile, so a displayed value can differ from the exact one by up to 0.5 second. Speed keeps two decimal places with a ±0.01 km/h tolerance, total time is a whole second, and distance keeps three decimal places with a ±0.001 unit tolerance. Do not chain rounded display values through another conversion; the error accumulates.

## Reading the result

Read the per-kilometre pace first, then the per-mile pace and speed; they describe the same performance. Average pace is useful for target conversion and post-race review, but it cannot show the race itself. It also cannot show effort: the same 6:00 per kilometre means different things in an easy run and a tempo run. Judge intensity with breathing, perceived effort and the purpose of the session.

## How to use it

1. Decide which question you are answering: pace from distance and time, time from distance and pace, or distance from time and pace.
2. Choose kilometres or miles, enter two finite values greater than zero, and write pace as `hh:mm:ss` or `mm:ss`.
3. Read the three outputs together and sanity-check them in the other unit.

## How to read the inputs: three common cases

| Mode | What you know | The two values you enter | Solved result |
| --- | --- | --- | --- |
| Distance + time | How far and how long | Distance, total seconds | Pace per km/mi, speed |
| Distance + pace | How far and the planned pace | Distance, pace seconds per unit | Total time, speed |
| Time + pace | Only a duration and a target pace | Total seconds, pace seconds per unit | Distance covered |

One common use is post-run review: enter the watch's moving time with the distance in distance-plus-time mode, read the average pace, and compare it with the planned pace. Another is pre-race target conversion: use distance-plus-pace to compute the total time, then check whether the half-way node stays reasonable. A third is treadmill translation: when the treadmill reports km/h, reverse it to an outdoor pace in time-plus-pace or distance-plus-time mode, and confirm the treadmill distance is a reading rather than a preset target.

Check units before entering: do not mix kilometres and miles, and write pace in whole seconds or minutes-seconds for the selected unit. If the units disagree — for example miles entered as distance and a per-kilometre pace — the tool interprets the pace in the selected distance unit and the whole result shifts. Only two of the three values are solved for; one value or all three cannot be resolved.

## Limits and when not to use it

Exactly two positive, finite values are required, and the tool does not judge whether the input is realistic. The course is treated as the full entered distance. A marathon is 42.195 km and a half marathon is 21.0975 km; entering 42.2 km returns the result for 42.2 km. The tool is not suitable for trail or ultramarathon execution plans, segment strategy, medical exercise prescription, or any claim that a pace equals an intensity.

## When this number misleads you

It only does steady-state arithmetic: supply two of distance, time and pace, and it returns the third. Treating a total time that includes traffic lights and aid-station stops as running time makes the pace systematically slow; equally, a pace derived from moving time cannot be used directly as a race target. Displayed seconds are rounded, so each value can be off by up to 0.5 s/km; repeatedly converting already-rounded values between kilometres and miles accumulates error, which can drift past 2 s/km after several round trips.

Do not use it to judge intensity, to correct for gradient, wind or altitude, or to extrapolate a race split plan. Turning a 5K pace into a marathon is not what this tool does; use the race prediction tool for cross-distance estimates and accept its own error. The result is not a training or medical prescription.

## Related reading

- [Easy running: how to set the intensity](/en/knowledge/easy-run/)
- [Training pace zones: how to set and use them](/en/knowledge/training-pace-zones/)
- [The marathon distance](/en/knowledge/marathon-distance/)
- [Split table: break a target time into segments](/en/tools/splits/)
- [Race-time estimate: the Riegel formula](/en/tools/race-predict/)

## Privacy and data

All calculations happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. File contents are never written into the URL. Clear the address-bar parameters after using a shared device.

## Sources and scope

The standard marathon distance and road-event context follow World Athletics; mile conversion uses the exact international mile; the distinction between pace and intensity follows the CDC talk-test description. The tool only performs arithmetic and does not certify a course or prescribe training. Verified 2026-11-06.

<!-- related-ring -->
## Related entries

- [Race-time estimate: the Riegel formula with a 1.06 exponent](/en/tools/race-predict/)
- [Result split analyzer: first/second-half fade, fade point and target gap](/en/tools/result-split-analyzer/)
- [Run-walk planner: schedule by cycles or total duration](/en/tools/run-walk/)
