---
entityId: tool:run-walk
locale: en
title: "Run-walk planner: schedule by cycles or total duration"
summary: "For run-walk training, enter run and walk durations, then list every segment by cycle count or total duration and state whether the final segment is truncated. Time arithmetic only, with no distance, pace or fitness estimate."
aliases: ["run-walk", "run walk intervals", "walk breaks"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

The run-walk planner turns “run for this long, walk for that long, repeat this many times” into a segment-by-segment sheet. It is for new runners, people returning after injury or a break, and runners who want a long session broken into manageable blocks. **Cycles mode** takes run seconds, walk seconds and a cycle count and lists every run and walk, including the walk in the final cycle. **Duration mode** takes the two segment lengths and a total duration, repeats them from the first cycle, and cuts the final segment at the boundary, marking it partial. If you need distance, calorie burn or a fitness estimate, this tool is not suitable.

## Calculation rules and limits

| Mode | Inputs | Scheduled total | Segment rule |
| --- | --- | --- | --- |
| Cycles | Run seconds, walk seconds, cycles | Cycles × (run + walk) | Run then walk each cycle; the last cycle is complete |
| Duration | Run seconds, walk seconds, total seconds | Exactly the entered total | Repeat until full; a crossing segment is cut and marked |
| Zero walk | Walk seconds = 0 | Run segments only | No zero-length walk rows |
| Totals | Segment list | Run total, walk total, full cycles | Summed from whole-second segments |

Both modes avoid “rounding up to a full cycle”. Duration mode ends exactly at the entered time; cycles mode ends exactly at cycles × single-cycle duration. The output includes requested time, scheduled time, full cycles, every segment, run total, walk total and whether the last segment is truncated.

## Worked example

- 120 s run, 60 s walk, 3 cycles: 540 seconds, 6 segments; 360 running and 180 walking.
- 120 s run, 60 s walk, total 400 seconds: two full cycles use 360 seconds, then a 40-second partial run; 280 running and 120 walking.
- 90 s run, 0 s walk, 2 cycles: 180 seconds, two run segments and no empty walk rows.

## Rounding and tolerance

All durations are whole seconds on input and output, so there is no fractional-second rounding and the sum of segments equals the scheduled total with a tolerance of zero. A non-integer run or walk duration such as 60.5 seconds is rejected rather than silently rounded. Cycles must be integers; total duration is capped at 604,800 seconds (seven days) and the plan at 3,000 segments.

## Reading the result

The sheet describes time structure, not intensity. It does not infer distance from duration or estimate pace, calories, VO2 max or injury risk. The number of alternations shows how dense the rhythm is; full cycles show how many complete repetitions were scheduled. All times are clock time and exclude warm-up, cool-down, fuel stops and travel.

## How to use it

1. Choose cycles mode when you know the repetition count, or duration mode when you know the total time.
2. Enter whole-second run and walk durations; run must be above zero, walk may be zero, then supply cycles or total duration.
3. Check the run total, walk total and truncation flag, then copy the segments to a watch or follow the first cycle.

## How to read the inputs: common cycle-count and duration cases

| Case | Run | Walk | Cycles / total | Scheduled result |
| --- | --- | --- | --- | --- |
| Fixed rounds | 120 s | 60 s | 3 cycles | 540 s, 6 segments, final complete |
| Fixed duration | 120 s | 60 s | 400 s | Two full cycles + a 40 s partial run |
| Running only | 90 s | 0 s | 2 cycles | 180 s, two run segments, no walk rows |
| Returning after injury | Short run | Longer walk | Per the week's plan | Time structure only, no intensity set |

First decide whether you know the number of rounds or the total time: use cycles mode for a fixed number of run-walk pairs, and duration mode to arrange running and walking inside a total session. Neither mode infers distance, so the same one-minute-on/one-minute-off pair covers very different ground at a jog and at a faster pace; this sheet cannot estimate mileage.

The run segment must be above zero and the walk segment may be zero. Non-integer seconds, cycle counts or total durations outside the limits return an error rather than a silent truncation. Keep warm-up, cool-down and waiting time out of the total, because every scheduled second belongs to a run or walk segment.

## Limits and when not to use it

Run duration must be a positive whole number of seconds and walk duration may be zero. Cycles range from 1 to 1,000; total duration is at most seven days; the plan is limited to 3,000 segments. These limits make the arithmetic executable, not the plan appropriate for your fitness or injury status. The tool does not judge whether a ratio is sensible. It is not suitable for distance- or pace-based sessions and is not a medical clearance. Seek qualified medical or sports advice if you are unwell, injured or at cardiovascular risk.

## When this number misleads you

It builds cycles by time, and the final segment ends the moment the requested duration is reached, so the realised run/walk ratio can drift from the ratio you set; the effect is larger when the duration or cycle count sits near the limits. The tool does not estimate distance or pace, so the same one-minute-on/one-minute-off covers very different distances at different paces. It also cannot judge whether that ratio suits your fitness, injury status or training phase.

Do not use it as an intensity prescription, a return-to-running clearance or a race time prediction; with pain, illness or cardiovascular risk, consult a qualified medical or sports professional. This tool is not medical advice.

## Related reading

- [The long run: distance, pace and execution](/en/knowledge/long-run/)
- [Return to running: stages and gates](/en/knowledge/return-to-running/)
- [What easy running really means](/en/knowledge/easy-run/)
- [Pace calculator: distance, time, pace and speed](/en/tools/pace/)

## Privacy and data

All calculations happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. Clear the address-bar parameters after using a shared device.

## Sources and scope

The run-walk structure follows the NHS Couch to 5K beginner plan, which starts with one-minute runs and 1.5-minute walks. The source illustrates a public format; it is not copied as a prescription and no ratio is claimed to suit everyone. Effort can be judged with the CDC talk test. Verified 2026-11-06.

<!-- related-ring -->
## Related entries

- [Split table: break a target time into segments](/en/tools/splits/)
- [Carb-load planner — a usable band from 10–12 g/kg/day over 36–48 hours](/en/tools/carb-load-planner/)
- [Race fuelling plan: estimate carbohydrate by the hour](/en/tools/fueling-planner/)
