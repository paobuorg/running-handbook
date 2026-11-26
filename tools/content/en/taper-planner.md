---
entityId: tool:taper-planner
locale: en
title: "Pre-race taper plan: drop volume over two or three weeks, keep pace"
summary: "Enter race distance, peak weekly km, peak long run, weekly quality sessions, taper weeks and days to race. The planner returns weekly volume, long run and quality session counts, last-week volume as a share of peak, the intensity retention mode, and warnings for a short window or low peak volume. Ratios are group-level research heuristics; observe your own recovery."
aliases: ["Pre-race taper plan", "taper planner", "taper week schedule"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

A taper is a planned reduction of training load before a race that lets accumulated fatigue clear while keeping training adaptations. Runners often go wrong in two directions: resting too completely in the final week so the legs feel stiff, or holding volume so high that race day still carries last week's fatigue. From your already-achieved peak weekly km, peak long run and weekly quality sessions, this tool builds a two- or three-week taper: weekly total and long run drop step by step, quality sessions shorten in distance and rep count while target pace stays unchanged. It also reports last-week volume as a share of the peak and warns when the taper window is too short or the marathon peak volume looks low.

It suits road and trail runners who have finished the pre-race peak and need the last two or three weeks arranged. It does not suit four situations. First, you have not reached your peak weekly volume yet; the ratios subtract from a peak, they do not build a plan from zero. Second, you want the table to schedule strength work, sleep, recovery or carbohydrate loading. Third, the race is within seven days and a full taper window cannot fit. Fourth, you show persistent fatigue, worse sleep or a raised resting heart rate, which calls for further reduction and a professional assessment rather than following a table.

## Inputs and units

Volume and long run are in kilometres; quality sessions are a weekly integer; taper weeks are 2 or 3; days to race are 0–28.

| Input | Unit | Required | Notes |
| --- | --- | --- | --- |
| `raceDistance` | enum | Yes | 5k / 10k / half / marathon / ultra |
| `peakWeeklyKm` | km | Yes | Peak weekly volume, greater than zero |
| `peakLongRunKm` | km | Yes | Peak long run, not negative |
| `qualitySessionsPerWeek` | sessions | Yes | 1–3 quality sessions per week |
| `taperWeeks` | weeks | Yes | 2 or 3 taper weeks |
| `daysToRace` | days | Yes | 0–28 days to race |

Peak weekly km means your highest week before the taper, not last week's volume; confirm the peak has actually occurred if recent weeks are still adding load. Quality sessions include intervals, tempo, pace work and steep trail efforts; easy runs do not count toward this count.

## Formula, assumptions and rounding

The planner validates the ranges first, then picks ratios by taper length.

| Taper weeks | Volume ratios | Long-run ratios | Quality, 1 session/week | Quality, 2–3 sessions/week |
| --- | --- | --- | --- | --- |
| 3 | 0.80 / 0.60 / 0.40 | 0.85 / 0.65 / 0.45 | 1 / 1 / 0 | 2 / 2 / 1 |
| 2 | 0.70 / 0.45 | 0.70 / 0.50 | 1 / 1 | 2 / 1 |

- Weekly volume = peakWeeklyKm × volume ratio.
- Long run = peakLongRunKm × long-run ratio.
- Last-week ratio = raw last-week volume ÷ peakWeeklyKm × 100, one decimal.
- Intensity retention is maintained: shorten session distance and rep count; keep target pace unchanged.

Warnings: days to race below taper weeks × 7 reports a window too short; marathon with peak weekly km below 30 reports a low peak-volume reference; the two warnings join into one string.

Rounding: weekly volume and long run round to the nearest whole kilometre; ratios apply to raw peak values before rounding; last-week share keeps one decimal. Assumptions: the peak week has already been delivered; target pace stays at race or threshold intensity; ratios are group-level endurance research conclusions, not an individual physiological prescription; the tool does not schedule strength, mobility, sleep, nutrition or carbohydrate loading; ultra and trail events may need longer tapers given cumulative fatigue and vertical load, so 2–3 weeks is a starting point.

## How to read the result

The result is a weekly table plus last-week share, intensity retention mode and warnings.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Weekly plan | Volume, long run, quality count and intensity note per week | Follow week by week; fill remaining mileage with easy runs |
| Last-week share | Last-week volume as a percentage of the peak | Below about 40% may cut too hard; above it the taper may be insufficient |
| Intensity retention | Whether pace is kept | What drops is distance and reps, not pace; do not turn quality sessions into easy jogs |
| Warning | Short window or low peak volume | Adjust week count or reassess race readiness per the warning |

Note that tapering is not "slower is better". The research consensus keeps training intensity while reducing total volume; skipping any fast rhythm leaves the body stiff on race day. The long run drops faster than weekly total, and the final week does not add another long run. When quality sessions shrink, keep one short session near race pace to activate the neuromuscular system. If the final week's volume looks too small, check whether the peak weekly km was entered correctly before adding volume back yourself.

## Worked example one: typical

Marathon, peak week 70 km, peak long run 30 km, two quality sessions per week, three taper weeks, 21 days to race.

| Week | Calculation | Volume | Long run | Quality |
| --- | --- | --- | --- | --- |
| W1 | 70 × 0.80; 30 × 0.85 = 25.5 | 56 km | 26 km | 2 |
| W2 | 70 × 0.60; 30 × 0.65 = 19.5 | 42 km | 20 km | 2 |
| W3 | 70 × 0.40; 30 × 0.45 = 13.5 | 28 km | 14 km | 1 |

Last-week share = 28 ÷ 70 × 100 = 40.0%. Days to race 21 equals 3 × 7, so the window is sufficient; peak 70 km is above the marathon low-volume threshold, so no warning. Intensity is maintained: each session shortens distance and reps while target pace stays unchanged.

## Worked example two: boundary

Half marathon, peak week 50 km, peak long run 21 km, one quality session per week, two taper weeks, 14 days to race.

| Week | Calculation | Volume | Long run | Quality |
| --- | --- | --- | --- | --- |
| W1 | 50 × 0.70; 21 × 0.70 = 14.7 | 35 km | 15 km | 1 |
| W2 | 50 × 0.45 = 22.5; 21 × 0.50 = 10.5 | 23 km | 11 km | 1 |

Last-week share = 22.5 ÷ 50 × 100 = 45.0%. Days to race 14 equals 2 × 7, so the window is sufficient; half distance does not trigger the marathon low-volume warning. This boundary matches a runner with one weekly quality session on a two-week taper; the second week keeps one short quality session.

## Worked example three: invalid or missing input

First invalid case: quality sessions entered as 0. The range is 1–3, so 0 is rejected as a range error on `qualitySessions` before any week is built.

Second: taper weeks entered as 1 or 4; only 2 or 3 are allowed, error field `taperWeeks`. Third: days to race negative or above 28, error field `daysToRace`. Fourth: peak weekly km entered as zero or non-numeric, rejected as range or not-finite. A race distance outside the five enum values raises an enum error.

## Relationship to knowledge and routes

The taper consensus is fairly consistent. Bosquet et al. (2007) found the two-week taper produced the largest endurance improvement, with volume reduced while intensity and frequency stayed maintained. Mujika and Padilla (2003) state the taper should maintain intensity, cut volume by up to 60–90%, and reduce frequency by no more than 20%, with an optimal duration from 4 days to over 28 days. The 2023 PLOS ONE meta-analysis of 14 studies associates a 41–60% volume reduction, maintained intensity and frequency, and up to 21 days of tapering with better time-trial performance, while noting that recovery varies between individuals. These readings connect to [strength and taper](/en/knowledge/strength-and-taper/) and [periodization](/en/knowledge/periodization/).

Load accumulation and overfatigue signs are covered in [load and overtraining](/en/knowledge/load-and-overtraining/), the full marathon structure in the [marathon training plan](/en/knowledge/marathon-training-plan/), and pre-race glycogen work in the [carb-load planner](/en/tools/carb-load-planner/).

## Common failure modes and early signals

The first failure mode is turning the taper into complete rest. Almost no running in the final week leaves stiff legs and a tight chest on race day. Early signal: several days with no movement and all quality sessions cancelled.

The second is cutting volume without cutting intensity, or cutting intensity only. The former leaves pace feeling soft; the latter keeps fatigue. Early signal: quality sessions all become easy jogs, or tempo sessions still run at peak-week distance.

The third is copying a three-week plan when the window is too short. Ten days to race cannot fit three taper weeks. Early signal: the tool warns the window is too short; compress to a two-week plan instead.

The fourth is ignoring individual variation. Some runners recover in three days, others need four weeks. Early signal: still tired after taper week one, with a high morning pulse or poor sleep; that means prior fatigue has not cleared, so cut further and watch.

## Limits

This tool plans running volume and long run for the 2–3 weeks before road and trail races; it does not replace a coach who individualises from training history, injury record and race feedback. It does not schedule strength work, cross-training, sleep, nutrition, fluid intake or carbohydrate loading, and it does not diagnose overtraining or injury. Ultra, multi-day and high-vertical events may need longer tapers. Persistent fatigue, sleep disturbance, abnormal heart rate or pain means stop following the table and consult sports medicine or a qualified coach.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, and the ratios draw on Bosquet 2007, Mujika & Padilla 2003 and the PLOS ONE 2023 taper review. No existing knowledge body was rewritten in this round.

## Related reading

- [Strength and taper: keeping intensity and mobility before race day](/en/knowledge/strength-and-taper/)
- [Periodization: peak, taper and race-week arrangement](/en/knowledge/periodization/)
- [Load and overtraining: recognising accumulated fatigue](/en/knowledge/load-and-overtraining/)
- [Marathon training plan: full race preparation structure](/en/knowledge/marathon-training-plan/)
- [Carb-load planner: pre-race glycogen storage](/en/tools/carb-load-planner/)

## Sources and scope

The two-week optimum and maintaining intensity and frequency come from the Bosquet et al. 2007 PubMed meta-analysis. Maintaining intensity, cutting volume by up to 60–90%, frequency down no more than 20%, durations over 4 days, and progressive non-linear tapers over step tapers come from the Mujika & Padilla 2003 review. The 41–60% volume reduction, maintained intensity and frequency, ≤21-day association with time-trial improvement, and individual variation come from the PLOS ONE 2023 systematic review and meta-analysis. The specific 2- and 3-week ratios, quality session counts and the 30 km marathon low-volume threshold are planning heuristics of this tool and do not appear verbatim in those papers. Verified 2026-11-25. Not covered: each runner's optimal taper duration, quality session format and injury-history effects require individual assessment.

<!-- related-ring -->
## Related entries

- [Grade-adjusted pace — converting hill pace to flat-equivalent pace with the Minetti polynomial](/en/tools/grade-adjusted-pace/)
- [Heat pace adjustment: estimate a slowdown from temperature and humidity](/en/tools/heat-adjust/)
- [Pace calculator: distance, time, pace and speed](/en/tools/pace/)
