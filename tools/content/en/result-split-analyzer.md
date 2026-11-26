---
entityId: tool:result-split-analyzer
locale: en
title: "Result split analyzer: first/second-half fade, fade point and target gap"
summary: "Enter cumulative checkpoints (km, elapsed minutes), target finish time and split granularity. The tool computes first- and second-half times, fade percent, fade-point km, pace variability, a rhythm verdict and the gap to target. It reviews a race after the fact; climbs, crowds and aid stops are not treated as fitness problems. The thresholds come from endurance pacing studies and are not medical or performance limits."
aliases: ["Result split analyzer", "result split analyzer", "segment pace analysis"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

After a race, the total time alone makes it hard to tell where pacing went wrong: did you surge early and fade later, or hold steady while the target was simply too high? This tool takes cumulative checkpoints, derives segment durations from adjacent differences, interpolates first- and second-half times by distance, computes second-half pace growth over the first, locates the first marked slowdown kilometre, reports pace variability, and classifies even, positive split or fade, with the gap to the target finish. Its job is to unpack the pace curve after the race, not to make real-time decisions on course.

It suits road marathon and trail runners with official split timing who review race rhythm, and those who compare a race's pace distribution against a training log. It does not suit three situations. First, checkpoints are unevenly spaced with large gaps, where half-split interpolation error grows. Second, you want to judge injury, fitness limits or whether to drop from segment pace alone. Third, the split recording mixes pauses, toilets or long aid stops; pace is dragged down by those stops. The tool assumes checkpoint times come from official timing; GPS pauses, crowd congestion and waits are not separated out.

## Inputs and units

One checkpoint per line as `km,elapsed minutes`; time also accepts `mm:ss` or `hh:mm:ss`. Elapsed time is the cumulative time to that point, not the segment duration.

| Input | Unit | Required | Range and notes |
| --- | --- | --- | --- |
| `splits` | rows | Yes | One `km,elapsed minutes` per line; 2–40 points, distances strictly increasing and elapsed time non-decreasing |
| `targetFinishMinutes` | min | Yes | Target finish time, 1–600 min |
| `splitKm` | km | Yes | Split granularity, 1, 5 or 10 km |

Enter the checkpoint's cumulative kilometre; elapsed time is the total time to that point. When the source gives only segment durations, accumulate them into elapsed times before entering. The target finish should be the pre-race planned duration, not the actual result worked back from the finish, so the gap reflects plan versus execution.

## Formula, assumptions and rounding

The tool validates the target finish and split granularity ranges first, then checks point by point that distances increase, elapsed time does not decrease and numbers parse.

- Segment duration = adjacent elapsed difference; segment pace = segment seconds ÷ segment distance (s/km).
- Total time = last elapsed time.
- First and second half: interpolate elapsed time at half the total distance between adjacent checkpoints.
- Fade percent = (second-half average pace ÷ first-half average pace − 1) × 100, one decimal.
- Fade-point km = the first segment whose pace exceeds the overall average pace by 15%; otherwise `null`.
- Variability = population standard deviation of segment paces ÷ mean pace × 100, one decimal.
- Verdict: fade ≥8% → `fade`; ≥2% → `positive-split`; otherwise `even`.
- Gap to target = total time − target finish, one decimal; positive means slower than target.

Main assumptions: checkpoints come from official timing, with GPS pauses, toilets and congestion not stripped out; pace comparison assumes level running, because climbs, descents and wind change segment pace independent of fitness; the 15% fade-point threshold and the 8%/2% rhythm bands are heuristics from endurance pacing studies, not universal medical or performance limits; halves are distance-based, and irregular checkpoint spacing widens interpolation uncertainty. Half times stay whole seconds; fade, variability and target gap keep one decimal.

## How to read the results

The result area gives first-half time, second-half time, fade percent, fade-point km, pace variability, rhythm verdict and target gap.

| Output | Meaning | How to use it |
| --- | --- | --- |
| First half | Elapsed seconds to the halfway mark | Compare with the second half for rhythm trend |
| Second half | Elapsed seconds from half to finish | The longer it grows, the clearer the fade |
| Fade percent | Second-half pace growth over the first | Near 0 is even; a high value suggests early surge or late fatigue |
| Fade-point km | First segment slowing clearly | Review climb, aid stop and body state around that kilometre |
| Pace variability | Segment pace standard deviation as a share of mean | A large value signals uneven segment rhythm |
| Verdict | `even` / `positive-split` / `fade` | Judge whether rhythm matched the race goal |
| Gap to target | Total time minus target finish | Positive slower than target, negative faster |

Note that a slow segment is not automatically a fitness problem; long climbs, descents, wind and crowds change segment pace. A positive split is common in long races, and marathon runners usually slow to some degree through the second half. A positive target gap means slower than target, negative means faster; an average pace near target does not prove even pacing, because early-fast and late-slow can cancel. Where the fade point overlaps the slowest segment, review that section's course conditions first.

## Case one: typical

Checkpoints: 10 km 30.0 min, 20 km 60.0 min, 30 km 92.0 min, 40 km 124.0 min; target finish 120 min, split granularity 10 km.

| Item | Calculation | Result |
| --- | --- | --- |
| First half | Linear interpolation at 20 km | 3600 s |
| Second half | 20 to 40 km | 3840 s |
| Fade percent | 3840 ÷ 3600 − 1 | 6.7% |
| Fade-point km | No segment over 15% above average | `null` |
| Pace variability | Segment pace stdev ÷ mean | 3.2% |
| Verdict | Fade 6.7%, between 2% and 8% | `positive-split` |
| Gap to target | 124.0 − 120 | +4.0 min |

The second half is 240 s slower than the first, a 6.7% fade, a mild positive split that does not reach the 8% `fade` threshold; no segment exceeds the average pace by 15%, so the fade point is empty. Variability is 3.2%, segment rhythm broadly steady; the finish is 4 minutes over target. This pattern reads as a slightly fast early pace with a small late fade, rather than a second-half collapse.

## Case two: boundary

Checkpoints: 10 km 30.0 min, 20 km 60.0 min; target finish 60 min.

| Item | Calculation | Result |
| --- | --- | --- |
| First half | Halfway at 10 km | 1800 s |
| Second half | 10 to 20 km | 1800 s |
| Fade percent | 1800 ÷ 1800 − 1 | 0.0% |
| Fade-point km | None | `null` |
| Pace variability | Equal segment paces | 0.0% |
| Verdict | Fade 0.0% | `even` |
| Gap to target | 60.0 − 60 | 0.0 min |

The two elapsed times are equal, each half 1800 s, fade 0.0%, variability 0.0%, verdict even, exactly on target. This boundary models ideal even execution; real races show pace variation from segment spacing, terrain and crowd flow.

## Case three: invalid or missing input

First, the second checkpoint's elapsed time 28.0 min is earlier than the first 30.0 min; elapsed time decreases, and the tool rejects it as an order error before computing pace, with error field `splits`. Second, fewer than two or more than forty points fail the count range; a non-numeric distance or a time that is empty or not `mm:ss` is named at the client line. Third, target finish 0, 700 min or non-finite is rejected as a range error with field `targetFinishMinutes`; split granularity 3 km, outside 1, 5 and 10, fails with field `splitKm`.

Fourth, an empty browser textarea parses as an empty list and reaches the calculation as an insufficient-points case; blank lines must not be counted as zero-second segments.

## Relation to routes and knowledge

Pacing profiles have a sport-science basis. A review classifies competition pacing as negative, all-out, positive, even, parabolic or variable; for prolonged events over about two minutes, even distribution of effort generally beats an early surge, and fatigue regulation is central to holding pace; well-trained ultra-endurance runners often adopt a positive profile that peaks early and fades gradually. A large marathon analysis treats slowing under 10% as maintaining pace and 30% as marked slowing; across more than ninety thousand finishes, mean pace change was about 15.6% for men and 11.7% for women, showing progressive second-half slowing is common. A separate study of nearly eighty thousand Boston finishers identified even, mild-positive, strong-positive and variable patterns; even-pacers finished fastest, and a pace decline above 20% in the final segment defines hitting the wall.

These map to daily training and records: race-day rhythm is in [race-day pacing](/en/knowledge/race-day-pacing/), training load and log comparison in [training log](/en/knowledge/training-log/), gait and metabolic metrics in [running-dynamics metrics](/en/knowledge/running-dynamics-metrics/); existing split recording is in [splits](/en/tools/splits/), and performance estimation in [race predictor](/en/tools/race-predict/).

## Common failure modes and early signals

The first failure mode is entering segment durations where cumulative elapsed time belongs, or the reverse. Cumulative checkpoint times are what this tool expects; mixing in segment durations compresses later elapsed times and distorts pace and both halves. Early signal: elapsed times shorten from checkpoint to checkpoint, or segment differences do not match the official splits.

The second is ignoring course conditions. Climbs are naturally slower and descents easier; a slow section should not be called a fitness drop without checking terrain. Early signal: the fade point follows a big climb or long descent.

The third is using the actual finish as the target finish. That pulls the gap toward zero and hides the plan-versus-execution difference; the target should be the pre-race plan. Early signal: review after review shows the target gap near zero, yet you cannot explain first-versus-second-half rhythm changes.

The fourth is treating study thresholds as personal limits. The 8%, 15% and 20% figures are group-study categories; an individual's fatigue point depends on training, heat, fueling and terrain. Early signal: a 12% slowdown after a long climb is read as a fitness collapse.

## Limits

The tool suits post-race rhythm review where official split timing exists, for road marathons and trail segments. It does not judge injury, fitness limits or drop decisions, does not correct pace differences from altitude, grade, wind, surface or crowds, and does not replace a coach's assessment of the training plan. It is not medical advice; dizziness, chest symptoms or persistent palpitations during a race should follow the race medical process. Study thresholds describe pacing distribution; concrete training goals and race strategy are set against personal training history.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, pacing classification comes from the Abbiss and Laursen pacing strategies review, slowdown grading from the ninety-thousand-plus marathon analysis, and the four patterns and wall threshold from the large Boston split study. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Race-day pacing: organising first and second half rhythm](/en/knowledge/race-day-pacing/)
- [Training log: load, sessions and race record comparison](/en/knowledge/training-log/)
- [Running-dynamics metrics: gait, ground contact and metabolism](/en/knowledge/running-dynamics-metrics/)
- [Splits: entering and saving race segments](/en/tools/splits/)
- [Race predictor: estimating from training and race performance](/en/tools/race-predict/)

## Sources and scope

Profile classification, even-effort benefit in long events and the ultra-endurance positive-profile tendency come from Abbiss and Laursen's 2008 pacing strategies review in *Sports Medicine*. The 10% maintain and 30% marked-slowing grades and the men's and women's mean slowdown come from the 2015 analysis of over ninety thousand US marathon performances. The four pattern shares, fastest even-pacers and 20% final-segment wall definition come from the 2026 large Boston Marathon split study. The half-split interpolation, 15% fade-point threshold, 8%/2% rhythm bands, population-stdev variability and rounding rules are this tool's implementation and are not in those studies. Verified 2026-11-25. Not covered: individual fatigue limits and course-specific grade pace adjustments require field conditions and coaching assessment.

<!-- related-ring -->
## Related entries

- [Run-walk planner: schedule by cycles or total duration](/en/tools/run-walk/)
- [Split table: break a target time into segments](/en/tools/splits/)
- [Carb-load planner — a usable band from 10–12 g/kg/day over 36–48 hours](/en/tools/carb-load-planner/)
