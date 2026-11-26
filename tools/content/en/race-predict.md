---
entityId: tool:race-predict
locale: en
title: "Race-time estimate: the Riegel formula with a 1.06 exponent"
summary: "Use one known road result to estimate another distance from 5 km to the marathon with the Riegel model, plus predicted pace. It is an empirical estimate, not a guarantee."
aliases: ["race predictor", "Riegel", "race time estimate"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

Enter the distance and finish time of a known road race, then a target distance. The tool applies the Riegel formula to estimate the target finish time and converts it to pace per kilometre, pace per mile and average speed. It is for runners who already have a comparable road result between 5 km and the marathon and want to know whether two target times are broadly at the same level. It is not for trail, ultramarathon or heavily climbed courses. If you have no comparable result, or training, body weight or injury status changed markedly between races, the estimate loses value and should not become a race goal.

## Formula and units

`Target time = known time × (target distance ÷ known distance)^1.06`

Distances are converted to metres and times to seconds internally; conversion to pace and speed happens only for display.

| Output | Calculation | Unit |
| --- | --- | --- |
| Predicted finish time | Known seconds × ratio^1.06 | Seconds, displayed whole |
| Distance ratio | Target distance ÷ known distance | Dimensionless |
| Pace per kilometre | Predicted seconds ÷ target kilometres | s/km |
| Pace per mile | Pace per km × 1.609344 | s/mi |
| Average speed | Target kilometres ÷ (predicted seconds ÷ 3600) | km/h |

Both distances must lie between 5,000 and 42,195 metres. The exponent is fixed at 1.06 as a product default; it is an empirical simplification, not a law for every runner or distance.

## Worked example

- 5,000 m in 1,200 s, target 10,000 m: ratio 2, estimate 1,200 × 2^1.06 = 2,501.918 → 2,502 s; about 250 s/km, 403 s/mi and 14.39 km/h.
- 10,000 m in 3,000 s, target 21,097.5 m: ratio 2.10975, estimate 6,619.209 → 6,619 s; about 314 s/km, 505 s/mi and 11.47 km/h.
- 21,097.5 m in 5,700 s, target 42,195 m: ratio 2, estimate 11,884.110 → 11,884 s; about 282 s/km, 453 s/mi and 12.78 km/h.

## Rounding and tolerance

Predicted time is rounded to the nearest whole second with a ±0.5-second tolerance. Pace per kilometre and per mile are also whole seconds with a ±0.5-second tolerance. Speed keeps two decimals with ±0.01 km/h, and the distance ratio is shown to six decimals. Do not feed a rounded displayed pace back into another conversion.

## Reading the result

Read the predicted time first, then the average pace. If the target pace is clearly faster than a pace you can currently sustain in training, the goal is probably aggressive rather than “one formula away”. The estimate provides no confidence interval, no probability of achieving the time, and no adjustment for weather, heat, altitude, course profile, start congestion or fuelling. Slowing in the second half of a long race is usually more complex than the formula; test the estimate with a shorter race or a tempo run before treating it as a goal.

## How to use it

1. Pick a road race between 5 km and the marathon with reasonably standard conditions, and enter its distance in metres and finish time in seconds.
2. Enter the target distance in metres, also within 5,000 to 42,195 metres.
3. Compare the predicted time and pace with your current sustainable training pace, then decide whether to use it as a goal or refine execution with a split table.

## How to read the inputs: picking a reference result

| Reference result | Target distance | Estimate value | Caveat |
| --- | --- | --- | --- |
| 5 km race | 10 km | Short-to-medium comparison | Small gap, limited exponent bias |
| 10 km race | Half marathon | Road long-distance extrapolation | Second-half slowing is more complex |
| Half marathon | Marathon | Long-distance extrapolation | Ratio 2, largest exponent assumption |
| Recent road race | Same distance | Result cross-check | Valid when conditions and training are comparable |

Choose a recent race on a standard course in normal weather as the reference. A result pushed through heat, or a first race after a break, does not represent current ability. Both distances are entered in metres; the formula works only on the distance ratio and ignores profile, altitude and surface.

If the two races are months apart, or volume, body mass or injury status changed clearly, recalibrate with a new result instead of reusing the old one. Treat the estimate as a starting point: test the target pace in a shorter race or tempo run before writing it into a race plan.

## Limits and when not to use it

The model is for road races only, not trail, ultramarathon or heavily climbed routes. It assumes comparable training, pacing and conditions between the two races, and the fixed 1.06 exponent is a simplification. It gives no probability, confidence interval or individual fit, does not replace a training plan and should not set training intensity on its own. If the races are far apart or fitness changed, reassess instead of reusing the old result.

## When this number misleads you

It fixes the exponent at 1.06 and assumes comparable training, pacing and conditions between the two races. The wider the distance gap, the more the exponent assumption matters: published comparisons of Riegel exponents of 1.07732 and 1.06 differ by about 10 seconds over 5 km, and the gap grows to minutes when a half marathon is extrapolated to a marathon. After a clear change in volume, body mass or injury status, an old result no longer represents current ability. Trail, ultra, big climbs and heat are outside the model, so entering them returns a precise-looking wrong number.

Do not use it for finish probabilities or confidence intervals, as a training pace prescription, or as medical or coaching advice.

## Related reading

- [Race-day execution: pacing, corrals and fuelling](/en/knowledge/race-day-pacing/)
- [5K and 10K training: from result to pace](/en/knowledge/5k-10k-training-plan/)
- [Pace calculator: distance, time, pace and speed](/en/tools/pace/)
- [Split table: break a target time into segments](/en/tools/splits/)
- [The marathon distance](/en/knowledge/marathon-distance/)

## Privacy and data

All calculations happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. Clear the address-bar parameters after using a shared device.

## Sources and scope

The formula and exponent background follows Blythe and Király (2016), “Prediction and Quantification of Individual Athletic Performance of Runners”, which describes fitting a constant per runner while fixing the exponent at 1.06; the 1.07732-versus-1.06 difference follows Blödorn and Döring (2025), “Running coefficients”, Scientific Reports; the standard marathon distance follows World Athletics. The tool guarantees no race result. Verified 2026-11-07.

<!-- related-ring -->
## Related entries

- [Result split analyzer: first/second-half fade, fade point and target gap](/en/tools/result-split-analyzer/)
- [Run-walk planner: schedule by cycles or total duration](/en/tools/run-walk/)
- [Split table: break a target time into segments](/en/tools/splits/)
