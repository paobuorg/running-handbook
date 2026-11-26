---
entityId: tool:trail-vertical-pacing
locale: en
title: "Trail vertical pacing planner: turn climb, descent and target time into executable pace"
summary: "Enter distance, climb, descent, target time and technicality to get equivalent distance, target pace, required climb rate, descent added time and a feasibility verdict. For pre-race budgeting and segment checks, not a substitute for course rehearsal."
aliases: []
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

Trail finish time is not “flat pace × distance”. Climb, descent and technicality change heart rate and muscle load at the same pace. This tool folds distance, climb, descent, target time and technicality into an equivalent distance, then gives target pace and required climb rate so you can see whether the plan is feasible.

It is a budgeting tool, not a substitute for course rehearsal. Before racing, calibrate with the actual course and your training data.

## Inputs and outputs

Inputs: distance (0.1–500 km), total climb (0–30,000 m), total descent (0–30,000 m), target time (0.25–60 h), technicality (low/medium/high). Outputs: equivalent distance, target pace, flat-equivalent pace, required climb rate, descent added time, feasibility and warnings.

Target time includes aid-station stops and technical slowdowns; do not enter “moving time only”.

## Formula and rounding

```
Equivalent distance = distance + climb / 100 + descent × factor / 100
Factor = 0.3 (low) / 0.5 (medium) / 0.8 (high)
Target pace = target time × 3600 / equivalent distance
Required climb rate = climb / target time
```

Equivalent distance and target pace round to integers; distance keeps one decimal. The formula is a planning approximation, not a physiological model.

## What equivalent distance means

Treating 100 m of climb as 1 km of flat is a budgeting approximation; it does not mean you actually run an extra kilometre, it converts vertical work into time cost. Descent is converted by the technical factor: harder terrain adds more. The conversion is suitable for a first “is the total time enough” screen, not for precise prediction.

## Choosing the technical factor

| Technicality | Factor | Suitable |
| --- | --- | --- |
| Low | 0.3 | Wide fire roads, little scree |
| Medium | 0.5 | Ordinary trail, roots and mixed scree |
| High | 0.8 | Steep, wet, night, technical rock |

A higher factor is more conservative; a lower factor underestimates descent time. For a first outing on a course, choose medium or high.

## Example 1: 50K, 2,000 m climb, 8 hours

| Item | Result |
| --- | --- |
| Equivalent distance | 80.0 km |
| Target pace | 360 s/km (6:00) |
| Flat equivalent | 576 s/km (9:36) |
| Required climb rate | 250 m/h |
| Feasibility | Feasible |

After folding 2,000 m climb and 2,000 m descent, the course is equivalent to 80 km; 6:00/km is the equivalent pace, not the actual pace of every kilometre.

## Example 2: 21.1K, 1,200 m climb, 3 hours

| Item | Result |
| --- | --- |
| Equivalent distance | 36.7 km |
| Target pace | 294 s/km (4:54) |
| Required climb rate | 400 m/h |
| Feasibility | Feasible |

For a short, climb-heavy course the equivalent pace looks fast, but execution is walk uphill, steady downhill and run the flats; do not take 4:54 to the flat and force it.

## Example 3: 100K, 5,000 m climb, 16 hours

| Item | Result |
| --- | --- |
| Equivalent distance | 190.0 km |
| Target pace | 303 s/km (5:03) |
| Required climb rate | 312 m/h |
| Feasibility | Feasible |

The equivalent pace does not look extreme, but 16 hours includes night, aid stops and technical sections; execute by segment table, not uniform pace.

## When it is infeasible

Required climb rate above 1,200 m/h or equivalent pace slower than 10:00/km is “infeasible”; above 800 m/h or 8:00/km is “at risk”. This is not a fitness verdict; it says the target time and course do not match, and you should add time, shorten distance or choose another course.

## Division of labour with grade-adjusted pace

[Grade-adjusted pace](/en/knowledge/grade-adjusted-pace-method/) answers “what flat pace does this climb feel like”; this tool answers “what climb rate and equivalent pace does the whole race require”. Calibrate a segment with the former, budget the race with the latter.

## Common errors

- Entering moving time only, excluding aid and technical stops.
- Choosing a low technical factor and underestimating descent and night.
- Treating equivalent pace as actual flat pace.
- Looking only at total time, with no segment table.
- Using the tool instead of course rehearsal and training calibration.
- Setting a target only a few minutes inside the cut-off, with no margin.

## Segment-table template

The tool budgets the whole race; execution needs segments. Split by aid stations into 4–6 segments, each with distance, climb, descent, target time and check item. At a station, check only that segment; do not recalculate the whole race.

| Segment | Distance | Climb | Descent | Target time | Check |
| --- | --- | --- | --- | --- | --- |
| 1 | 0–12 km | 600 m | 300 m | 1:40 | Breathing, heart rate |
| 2 | 12–25 km | 900 m | 500 m | 2:10 | Fuel, legs |
| 3 | 25–38 km | 700 m | 800 m | 2:20 | Feet, night light |
| 4 | 38–50 km | 300 m | 400 m | 1:10 | Safe finish |

Segment times should sum close to the tool's target; if they differ greatly, change the segments, not the formula.

## Pair with the climb-rate table

This tool calculates the required climb rate; [Trail vertical pacing](/en/knowledge/trail-vertical-pacing/) gives what you can sustain. If the tool requires 900 m/h and your training sustains 600 m/h, the plan is not feasible: add time, shorten distance or change course, not force it on race day.

## Three failure cases

**Case 1: 8-hour target with 3,000 m climb.** Required 375 m/h looks feasible, but a low technical factor and underestimated descent may make it 10 hours; recalculate with “high”. **Case 2: 100K in 14 hours with 6,000 m climb.** Required 429 m/h, but night and aid stops add time; the segment table must include stops. **Case 3: half marathon with 1,000 m climb in 2 hours.** Equivalent pace may look fast, but technical descent cannot be run at flat pace; calibrate by rehearsal, not by forcing the table.

## Leave margin in the target

Do not set the target against the cut-off. Keep at least 10–15% for weather, queues, navigation errors and feet; 15–20% for 100K and night races. “Feasible” means the arithmetic holds, not that there is margin.

## Ten-minute pre-race review

Copy the output onto a pace card: equivalent pace, required climb rate, descent added time, target time. On race day execute the segment table; do not reopen the calculator at every station. Use waterproof paper or a photo, not phone signal.

Check three things: 10–15% margin in the target, technical factor chosen for the worst terrain, aid-station stops included. All three pass before the card goes on the course.

## Related reading

- [Trail vertical pacing](/en/knowledge/trail-vertical-pacing/)
- [Grade-adjusted pace](/en/knowledge/grade-adjusted-pace-method/)
- [Grade-adjusted pace tool](/en/tools/grade-adjusted-pace/)

Change note: new tool documentation with three cases, four sources, segment suggestions and boundary statements; the knowledge page had the method but no way to split distance, climb and technical difficulty into segments. Still open: the tool is not an official cutoff sheet and does not replace reconnaissance or weather judgment.
