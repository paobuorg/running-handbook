---
entityId: tool:cutoff-planner
locale: en
title: "Cutoff buffer planner: check each checkpoint against the official cutoff table"
summary: "Enter the course distance, start time, target finish, finish cutoff and per-checkpoint cutoffs. Using an even-pace assumption, the tool projects arrival at each checkpoint, its buffer, the target and cutoff paces, and the tightest point. It is a pre-race planning aid, not a replacement for official race rules, how you feel on site, or medical judgement."
aliases: ["Cutoff buffer planner", "cutoff planner", "checkpoint buffer calculator"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

Once you have an official cutoff table for a trail race or marathon, the common mistake is to look only at the finish cutoff and assume "several hours left" is enough. Cutoff pressure usually concentrates at a handful of mid-race aid stations: climbs, queued fluid stops, and the slowdown after dark can bring you to the time barrier for the first time there. This tool places the official cutoff table next to your target finish time, projects an arrival clock and buffer at each checkpoint under an even-pace assumption, reports the pace required by your target and the slowest pace allowed by the finish cutoff, and names the tightest point. It returns one of three verdicts: feasible, at-risk, or infeasible.

It suits runners who already have an official split cutoff table and want a pre-race pacing plan, and crew who want to judge where buffers are thin in advance. It does not suit three situations. First, when the race publishes only an overall time limit and no checkpoint cutoffs. Second, when you want to predict rankings or compare yourself to other runners. Third, when you are already on course and need to decide whether to drop; that decision follows race officials, medical staff and how you feel. The even-pace assumption is only a starting point for trail racing, where climbs, heat, waits, night fatigue and aid-station stops all move real arrival times.

## Inputs and units

All clock inputs are 24-hour `HH:MM` strings converted to minutes since midnight internally. Distance is in kilometres; pace output is seconds per kilometre; buffers are in minutes.

| Input | Unit | Required | Notes |
| --- | --- | --- | --- |
| `distanceKm` | km | Yes | Course distance, greater than zero; use the official race distance |
| `startClock` | HH:MM | Yes | Gun or mat-start time |
| `targetFinish` | HH:MM | Yes | Planned finish clock; must be later than the start |
| `finishCutoff` | HH:MM | Yes | Finish cutoff clock; must not be earlier than the target finish |
| `checkpoints` | rows | Yes | One row per point: `km,cutoff`; km strictly increasing and within the course; may be empty |

Checkpoints are entered one per line, for example `21,10:00` means the cutoff at 21 km is 10:00. If the race table uses miles, convert to kilometres first. If a point is marked as a default cutoff identical to the next station, enter the actual clock from the official table.

## Formula, assumptions and rounding

The planner converts start, target finish and finish cutoff to minutes since midnight and checks the order: start must be earlier than the target finish, and the target finish must not be later than the finish cutoff; otherwise it raises an order error.

- Required pace (s/km) = (target finish − start) × 60 ÷ distanceKm.
- Cutoff pace (s/km) = (finish cutoff − start) × 60 ÷ distanceKm.
- Predicted arrival at a checkpoint = start + checkpoint km × required pace ÷ 60.
- Buffer at that checkpoint = checkpoint cutoff − predicted arrival.
- The tightest checkpoint is the one with the smallest raw buffer; finish buffer = finish cutoff − target finish.

Verdict rules: any checkpoint buffer below zero is infeasible; otherwise the smallest raw buffer below 15 minutes is at-risk; everything else is feasible. The 15-minute threshold is a planning heuristic, not an official race rule.

Rounding order: paces round to the nearest whole second per kilometre; buffers and the finish buffer round to the nearest whole minute; verdict thresholds are compared on unrounded raw buffers so early rounding cannot flip a boundary. Key assumptions: pace is constant across the race, with no model for climbs, heat, stops or negative splits; all clocks fall on the same day, with no after-midnight handling; checkpoint cutoffs are read as deadlines to leave the station; the target finish is a planned goal, not a performance prediction.

## How to read the result

The result block has six fields, best read together with the checkpoint table.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Target pace | Average pace implied by the target finish | Reference for training runs and race-day split targets |
| Cutoff pace | Slowest average pace implied by the finish cutoff | Only a theoretical margin; never a training pace |
| Tightest checkpoint | Smallest buffer, shown as `km 21` | Watch this point's arrival and stop duration on race day |
| Tightest buffer | Minutes left at the tightest point | Below 15 minutes means the cutoff can catch you mid-race |
| Finish buffer | Finish cutoff minus target finish | Larger is calmer; zero means the target touches the cutoff line |
| Verdict | Feasible / at-risk / infeasible | Infeasible means revising the target or training; at-risk means holding buffer around the tightest point |

Note that the cutoff pace being slower than the target pace only means you can theoretically finish within the cutoff; it does not mean finishing at that pace is safe. Trail cutoff tables are usually generous early and tighter later, and queuing, changing layers and treating blisters at stations consume buffer. If the tightest point is in the second half, night fatigue adds another penalty. A feasible verdict does not mean you can relax; it only means every buffer stays above 15 minutes under the even-pace projection.

## Worked example one: typical

Course 42 km, start 08:00, target finish 11:30, finish cutoff 12:00; checkpoint at 21 km cuts off at 10:00, and 32 km at 11:00.

| Item | Calculation | Result |
| --- | --- | --- |
| Target pace | (11:30 − 08:00) = 210 min; 210 × 60 ÷ 42 | 300 s/km (5:00/km) |
| Cutoff pace | (12:00 − 08:00) = 240 min; 240 × 60 ÷ 42 = 342.857 | 343 s/km |
| 21 km arrival | 08:00 + 21 × 5 min | 09:45, buffer 15 min |
| 32 km arrival | 08:00 + 32 × 5 min | 10:40, buffer 20 min |
| Tightest point | 21 km, 15 min buffer | `km 21` |
| Finish buffer | 12:00 − 11:30 | 30 min |

The smallest buffer, 15 minutes, sits exactly on the lower edge of feasible, so the verdict is feasible. In practice a climb or a long stop around 21 km can spend that 15 minutes quickly; treat this as "just feasible", not "comfortable margin".

## Worked example two: boundary

Course 10 km, start 08:00, target finish 09:00, finish cutoff 10:00, with no checkpoints entered.

| Item | Calculation | Result |
| --- | --- | --- |
| Target pace | 60 × 60 ÷ 10 | 360 s/km |
| Cutoff pace | 120 × 60 ÷ 10 | 720 s/km |
| Finish buffer | 10:00 − 09:00 | 60 min |
| Tightest point | No checkpoints | Empty; finish buffer is the only buffer |

An empty checkpoint list is allowed; the verdict then follows the finish only. A 60-minute buffer is above 15 minutes, so the verdict is feasible. This boundary matches road races with an overall limit but no split cutoffs; the tool does not invent checkpoints.

## Worked example three: invalid or missing input

First invalid case: start 10:00, target finish 09:30. The target is earlier than the start, violating the start < target rule, so the planner raises an order error on `targetFinish` before any pace is computed.

Second: a checkpoint km beyond the course distance, or two rows whose km values are not strictly increasing, is rejected as a range error on `checkpoints`. Third: a row written `21 10:00` without a comma, or a clock such as `25:00`, fails parsing on the client and raises a format error naming the line; it never reaches the library calculation.

A missing required field leaves the browser input empty and produces a non-finite number, handled as a not-finite error. Do not treat an empty string as zero minutes.

## Relationship to routes and knowledge

Cutoff rules differ by race format. UTMB series regulations state that runners must leave the checkpoint or aid station before the cutoff time, and leaving after the time barrier leads to disqualification; with waved starts, barriers are calculated from the last wave. The Western States 100 aid-station chart lists a cutoff per station, states that cutoffs are strictly enforced and that missing one means you must stop, and notes that cutoff times are not a pacing guide. These official readings are recorded in the [UTMB](/en/routes/utmb/) and [Western States 100](/en/routes/western-states/) route profiles.

The target pace here is an even-pace back-calculation; race-day rhythm is covered in [race-day pacing](/en/knowledge/race-day-pacing/), pre-race load and tapering in [periodization](/en/knowledge/periodization/), and race-day items and checks in the [race checklist](/en/tools/race-checklist/).

## Common failure modes and early signals

The first failure mode is treating the cutoff pace as a training pace. The cutoff pace is a theoretical slowest average; training by it sets an over-conservative goal and ignores the front-loaded generosity of cutoff tables. Early signal: training at the cutoff pace still feels easy, yet the target finish keeps slipping.

The second is watching only the finish cutoff and ignoring split buffers. Many runners are pulled at a mid-race station, not at the finish. Early signal: a climb leaves you ten or more minutes late, and the next station queue adds another ten.

The third is ignoring wave starts and start intervals. In waved races, barriers follow the last wave; early-wave runners cannot apply later-wave clocks directly. Early signal: the cutoff table labels waves while you entered your own start clock.

The fourth is overestimating evenness. Late-race pace usually drops noticeably, so the even projection is optimistic in the second half. Early signal: recent long runs fade by more than 10% after halfway, yet you still project arrivals from first-half pace.

## Limits

The tool suits pre-race planning for road marathons and trail races completed within one day and backed by an official split cutoff table. It does not handle after-midnight cutoffs, and it does not model altitude, climbs, surface, heat, wind, aid stops or night fatigue, nor does it judge whether you are fit to finish. It is not medical advice; dizziness, nausea or chest symptoms should follow the race medical process rather than a pace table. If official rules change, waves are adjusted, or a cutoff moves early, follow the on-site announcement.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, and the cutoff wording comes from the UTMB regulations and the Western States 100 official aid-station page. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Race-day pacing: organising first and second half rhythm](/en/knowledge/race-day-pacing/)
- [Periodization: taper, peak and pre-race arrangement](/en/knowledge/periodization/)
- [Race checklist: gear and race-day checks](/en/tools/race-checklist/)
- [UTMB route profile and cutoff rules](/en/routes/utmb/)
- [Western States 100 route profile and aid-station chart](/en/routes/western-states/)

## Sources and scope

The enforcement wording (leave before the cutoff, disqualification after the barrier, last-wave calculation for waved starts) comes from the official UTMB World Series regulations. The per-station chart, the "miss the cutoff and you must stop" rule, the "cutoffs are not a pacing guide" note, and the asterisk default-cutoff explanation come from the official Western States 100 aid-station page. The 24-hour and 30-hour finish cutoffs and spectator and assistance restrictions come from the official Western States FAQ. The 15-minute risk threshold, even-pace arrival projection and buffer arithmetic are planning heuristics of this tool and are not in those official sources. Verified 2026-11-25. Not covered: specific 2027 cutoff minutes for each race follow that season's official handbook on the race website.

<!-- related-ring -->
## Related entries

- [Race checklist: generated by surface, duration and weather](/en/tools/race-checklist/)
- [Race-day timeline planner: work backward from the gun to wake-up and every reserve](/en/tools/race-day-timeline/)
- [Race qualifier checker: compare your result against the official standard, buffer and missing conditions](/en/tools/race-qualifier-checker/)
