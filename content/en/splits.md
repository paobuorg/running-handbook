---
entityId: tool:splits
locale: en
title: "Split table: break a target time into segments"
summary: "Enter total distance, total time and split distance, then choose an even or negative-split strategy to build a printable table. The final segment may be short, and all whole seconds add up exactly to the total."
aliases: ["split table", "negative split", "pace splits"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What it is for

A split table breaks a target performance into equal-distance segments. It is for runners with a defined target time who need a pace band or an aid-station note. It offers two arithmetic strategies: **even** and **negative split**. Both are planning tools, not predictions. If the target time is undecided, or the course is hilly enough to need grade-adjusted pacing, this table is not a substitute for course analysis and coaching.

## Calculation rules and strategies

**Even**: every metre uses the same pace, total time ÷ total distance.

**Negative split**: the first half is slower and the second half faster. `delta` defaults to 0.02 and is limited to 0 to 0.10. The first half uses `(1 + delta) ÷ 2` of total time and the second half uses `(1 − delta) ÷ 2`. A segment crossing the midpoint is integrated over its actual metres in each half.

| Step | Rule | Note |
| --- | --- | --- |
| 1 | Split count = ⌈total distance ÷ split distance⌉ | The final segment may be shorter |
| 2 | Segment i covers [(i−1)×split, min(i×split, total)] | Starts at zero and ends at the total |
| 3 | Even: exact time = segment metres × total seconds ÷ total metres | One pace for every segment |
| 4 | Negative: multiply the half before/after the midpoint by its own pace | Cross-midpoint segments add both parts |
| 5 | Floor each exact time, then allocate leftover seconds by largest remainder | Largest fractions gain one second; ties go to the earlier split |

Largest-remainder allocation can put a segment one second away from its exact value, but the total does not drift. Cumulative times use allocated whole seconds, so the last segment cannot turn negative.

## Worked example

- 10 km, 3000 seconds, 1 km even splits: 10 segments of 300 seconds, cumulative 300 to 3000.
- 5 km, 1500 seconds, 2 km even splits: 3 segments of 2, 2 and 1 km at 600, 600 and 300 seconds.
- 10 km, 3000 seconds, 4 km negative splits, delta = 0.02: exact times 1224, 1188 and 588 seconds; the second segment crosses halfway.

## Rounding and tolerance

Exact durations are floored and the remainder is redistributed in whole seconds. Each segment can differ from its exact value by at most one second, while the sum equals the entered total exactly. Total time must be a whole number of seconds, otherwise the tool rejects the input.

## Reading the result

The numbers are targets, not forecasts. The cumulative column tells you what the clock should read at each checkpoint. If the first half is clearly faster than the table, the second half may pay for it. A negative-split table describes a deliberate distribution; it does not promise that the second half will feel easier or that the pace will hold when tired. It cannot show hills, wind, aid stops, start congestion or heat.

## How to use it

1. Set the total distance, target time in whole seconds and split distance, and choose kilometres or miles.
2. Choose even or negative splits; for negative, set delta from 0 to 0.10, defaulting to 0.02.
3. Copy the cumulative times onto a pace band and rehearse the same structure in training before race day.

## Limits and when not to use it

Total distance, total time and split distance must be greater than zero. Delta applies only to negative splits and a zero delta reproduces the even table. A split distance larger than the total produces one segment equal to the total time. The tool does not adjust for hills, aid stations or weather and gives no finish probability or training plan. It suits neither trail pacing that depends on terrain and aid points nor exploratory runs without a target time.

## When this number misleads you

The table supports only two shapes: even pace all the way, or one pace before halfway and a faster one after. The 0.02 delta is a default example, not an optimum, and pushing it to 0.10 does not make it a good tactic. It assumes equal splits (the last may be short) and exact conservation of total time, while hills, headwind, aid-station stops and crowds are not modelled. Enter a total time that includes stops and the whole table runs slow.

Do not use it for trail or ultra split planning, for finish probabilities, or in place of race-day tactical judgement; it is not training or medical advice.

## Related reading

- [Race-day execution: pacing, corrals and fuelling](https://learn.paobu.org/en/articles/race-day-pacing/)
- [Training pace zones: how to set and use them](https://learn.paobu.org/en/articles/training-pace-zones/)
- [Pace calculator: distance, time, pace and speed](https://tools.paobu.org/en/tools/pace/)

## Privacy and data

All calculations happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. Clear the address-bar parameters after using a shared device.

## Sources and scope

Distance units and the standard marathon value follow World Athletics; the distinction between a pace distribution and training intensity follows the CDC talk-test description. The table is arithmetic only and is not a finish-time promise. Verified 2026-11-06.
