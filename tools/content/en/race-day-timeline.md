---
entityId: tool:race-day-timeline
locale: en
title: "Race-day timeline planner: work backward from the gun to wake-up and every reserve"
summary: "Enter the start time, wave offset, travel and parking, check-in, bag drop, warm-up duration and target finish time. Working backward, the tool projects effective start, wake, departure, arrival, check-in, bag drop, warm-up and finish clocks, plus the full milestone chain. It is a pre-race planning aid, not a replacement for official shuttles, security, corral close times or on-site judgement."
aliases: ["Race-day timeline planner", "race day timeline", "pre-race back-calculator"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

The common race-morning chaos happens before the start gun, not after it. The alarm goes off at the usual weekday time, the car park is full, bag check and toilets queue at the village, the warm-up shrinks to a few bounces on the spot, and you reach your corral a minute before the gun. This tool fixes the start time as an anchor and projects backward through wave offset, travel, check-in, bag drop and warm-up. It produces a wake-to-finish timeline with a clock for every milestone; when a block is left at zero, or the chain falls before midnight, the timeline flags it.

It suits road marathon and trail runners who know their start time and need to arrange accommodation, departure rhythm and pre-race preparation, and crew who plan shuttles and hand-offs in advance. It does not suit three situations. First, when the race uses waved starts and you do not yet know your wave. Second, when the venue has special rules for luggage, security or bag check that the current guide describes in detail; those follow the on-site process. Third, when you want to predict race performance or plan mid-race pace, which belongs to a pacing tool. The clocks the tool returns are planning projections, not commitments: queues, finding the corral, another toilet visit and a longer warm-up can all consume the reserve.

## Inputs and units

The start time is a 24-hour `HH:MM` string converted to minutes since midnight internally. Preparation blocks are entered in minutes; the target finish duration is in hours. Zero is allowed, but every field has a cap.

| Input | Unit | Required | Range and notes |
| --- | --- | --- | --- |
| `startClock` | HH:MM | Yes | Gun time, 00:00–23:59 |
| `waveOffsetMinutes` | min | Yes | Delay of your wave after the unified gun, 0–90 |
| `travelMinutes` | min | Yes | Door-to-venue commute and parking, 0–180 |
| `checkinMinutes` | min | Yes | Check-in, gear verification and corral entry, 0–120 |
| `bagDropMinutes` | min | Yes | Bag drop and toilets reserve, 0–120 |
| `warmupMinutes` | min | Yes | On-course warm-up duration, 0–60 |
| `finishTargetHours` | hours | Yes | Target finish duration, 0–12 |

When filling it in, count the travel block from lodging to the venue, including parking, walking to the entrance and the outer concourse; do not enter driving time only. The check-in block includes queues rather than the ideal time to finish one errand. The bag/toilet block includes queues. The warm-up block counts actual running and dynamic movement, not time spent waiting for a warm-up area. If you stay within walking distance, enter walking minutes; if a shuttle is required, add its departure interval to the travel reserve.

## Formula, assumptions and rounding

The tool validates the start-clock format first, then checks that each minute block and the finish duration are within range. It projects backward from the effective start: the warm-up occupies the last `warmupMinutes` before the start; bag drop sits before the warm-up; check-in sits before bag drop; a fixed 10-minute on-site buffer follows arrival; departure then projects back over travel; wake is 90 minutes before departure.

- Effective start = gun + wave offset.
- Warm-up start = effective start − warm-up duration.
- Bag drop finish = warm-up start − bag-drop reserve.
- Check-in finish = bag-drop finish − check-in reserve.
- Venue arrival = check-in finish − 10-minute fixed buffer.
- Departure = venue arrival − travel time.
- Wake = departure − 90-minute fixed prep.
- Estimated finish = effective start + target finish hours × 60.

The main assumptions are: all times are on race morning; a milestone that falls before midnight wraps to the previous day and is flagged on the timeline. Travel covers door-to-venue movement and parking but not ticket, security or crowd queues. The warm-up sits immediately before the gun, with no separate pre-race stride-out, dedicated stretching or post-warm-up fluid. The 10-minute arrival buffer and 90-minute wake prep are planning heuristics, not official requirements. Clocks are planning projections, and official corral close times, shuttles and venue opening must be checked against the current race guide. Rounding keeps every clock at the nearest whole minute and converts finish hours to whole minutes, with no fractional minute retained.

## How to read the results

The result area gives eight key clocks first, then a milestone table ordered from wake to finish.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Effective start | When you actually cross the line after the wave offset | Check corral open/close times, so warm-up and bag drop project from the right clock |
| Wake | Front of the chain: when you must get up | Work back to alarm, breakfast and changing time |
| Departure | When you leave the lodging or starting point | Check shuttle, parking and walking feasibility |
| Venue arrival | End of travel, entry to the outer venue area | Spot whether the travel reserve is too short |
| Check-in finish | Verification done, ready for bag drop | Schedule crew hand-off and gear checks |
| Bag drop finish | Bag drop and toilets done, ready to warm up | Plan clothing storage hand-off |
| Warm-up start | When the warm-up begins | Plan warm-up content so it does not run into the gun |
| Estimated finish | Finish clock implied by the target duration | Plan shuttles, family meeting and post-race arrangements |
| Milestone chain | Wake, departure, arrival, check-in, bag drop, warm-up, start, finish in order | Spot a block that is too short, or a chain that falls on the previous day |

Note that the eight clocks form a tight chain; blocks touching end to end does not mean the plan is ideal. In reality, finding the corral, taking photos and meeting friends add waiting time. The fixed 10-minute arrival buffer and 90-minute wake prep are already inside the chain and should not be entered again. A zero block still returns a timeline, but that step usually needs real time on race morning.

## Case one: typical

Gun 07:30, wave offset 10 minutes, travel and parking 30 minutes, check-in 15 minutes, bag drop 10 minutes, warm-up 10 minutes, target finish 3.5 hours.

| Item | Calculation | Result |
| --- | --- | --- |
| Effective start | 07:30 + 10 | 07:40 |
| Warm-up start | 07:40 − 10 | 07:30 |
| Bag drop finish | 07:30 − 10 | 07:20 |
| Check-in finish | 07:20 − 15 | 07:05 |
| Venue arrival | 07:05 − 10 | 06:55 |
| Departure | 06:55 − 30 | 06:25 |
| Wake | 06:25 − 90 | 04:55 |
| Estimated finish | 07:40 + 210 | 11:10 |

The chain touches end to end with no waiting buffer. Large road races commonly advise arriving about 60 minutes early for bag check, toilets and corral entry; here the wake-to-start reserve is 165 minutes, of which travel, check-in, bag drop and warm-up total 65 minutes and the rest is wake prep and the arrival buffer. The warm-up starts at 07:30 with ten minutes to the effective start, a short warm-up suited to a race morning after good prior activation; a longer trail race that needs fuller dynamic activation should extend the warm-up block or arrive earlier.

## Case two: boundary

Gun 08:00, wave offset, travel, check-in, bag drop and warm-up all zero, target finish 0 hours.

| Item | Calculation | Result |
| --- | --- | --- |
| Effective start | 08:00 + 0 | 08:00 |
| Warm-up start | 08:00 − 0 | 08:00 |
| Bag drop finish | 08:00 − 0 | 08:00 |
| Check-in finish | 08:00 − 0 | 08:00 |
| Venue arrival | 08:00 − 10 | 07:50 |
| Departure | 07:50 − 0 | 07:50 |
| Wake | 07:50 − 90 | 06:20 |
| Estimated finish | 08:00 + 0 | 08:00 |

All preparation blocks at zero are inside the input ranges, so the tool still returns a full timeline instead of throwing; the fixed 10-minute arrival buffer and 90-minute wake prep remain, so arrival, departure and wake do not collapse onto the gun. This boundary models the extreme assumption that the venue is at the door and no preparation is needed; it is not a normal race-morning arrangement, because bag check, queues and body activation all take real time.

## Case three: invalid or missing input

First, the start time is written `07:65`; the minute field is outside 00–59, so the tool rejects it as a format error before projecting any block, with error field `startClock`. Second, the wave offset is 100 minutes, outside 0–90; travel is 200, outside 0–180; check-in or bag drop is 150, outside 0–120; warm-up is 70, outside 0–60; or the finish duration is −1 hour, below 0; the tool rejects these as range errors with fields `waveOffsetMinutes`, `travelMinutes`, `checkinMinutes`, `bagDropMinutes`, `warmupMinutes` and `finishTargetHours` respectively.

Third, an empty browser field yields a non-finite number; the tool treats it as a non-finite error rather than turning an empty string into zero minutes. Fourth, when travel, check-in or bag-drop reserve is so long that the wake milestone falls before midnight, the tool wraps that milestone to the previous day and flags it on the timeline. In that case reassess accommodation or shorten another preparation block rather than treating the previous day as a normal morning.

## Relation to routes and knowledge

Official race procedures set out the pre-race sequence. New York Road Runners' race procedures guide runners who picked up their bib in advance to arrive at least 60 minutes before the start for bag check, toilets and corral entry, to be in their corral at least 10 minutes before the gun, and note that bib pickup closes 10 minutes after the start. The New York City Marathon start page adds that wave and corral appear on the bib, runners may move to a later or slower corral but not an earlier one; corrals open and close on a published schedule; finish time is the net time from crossing the start line; the start village has more than 1,600 toilets, only the clear official village bag enters Fort Wadsworth, and bags are inspected. Read these alongside the [New York Marathon](/en/routes/new-york/) and [Boston Marathon](/en/routes/boston/) route profiles.

Warm-up has a research basis. A warm-up study in recreational endurance runners compared running plus static stretching, running plus dynamic stretching, and running alone; the structure was ten minutes of running plus five minutes of stretching. Both stretching variants improved running economy and lowered perceived exertion. This justifies keeping a separate warm-up block, but stretching duration is not beneficial without limit; very long stretches show no extra gain. The full morning sequence is covered in [race-morning protocol](/en/knowledge/race-morning-protocol/), race-day rhythm in [race-day pacing](/en/knowledge/race-day-pacing/), and carry-on checks in the [race checklist](/en/tools/race-checklist/).

## Common failure modes and early signals

The first failure mode is counting travel as driving time only. Parking, walking to the start and clearing the outer security area sit outside the drive, so real door-to-venue time is usually longer than navigation predicts. Early signal: you enter the shortest navigation commute and ignore morning peak traffic and a saturated car park.

The second is treating bag drop and toilets as skippable. Queues for bag check and toilets are heaviest in the twenty minutes before the gun and slower closer to the start. Early signal: your previous races lost the warm-up to bag or toilet queues, yet this block is still set to zero.

The third is letting the warm-up run to the last minute. A warm-up leaves you activated when it ends, but the state fades after a gap; starting too late, on the other hand, forces effort before the muscles are ready. Early signal: the warm-up content matches training sessions but only five minutes are reserved.

The fourth is ignoring waved starts. Corral close times and shuttles follow the wave schedule; early and late waves do not share one morning routine. Early signal: the guide labels wave times while you entered a unified gun time.

## Limits

The tool suits pre-race planning for road marathons and trail races with a known morning start time. It does not handle after-midnight starts, and it does not model traffic delays, security queues, weather hold-ups or aid stops, nor longer-cycle matters such as breakfast digestion, changing clothes or recovery. It is not medical advice; dizziness, chest symptoms or palpitations on race morning should follow the race medical process rather than the timeline. When the current guide sets special rules for bags, shuttles, corral opening or traffic control, the on-site announcement governs.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, the pre-race wording comes from the official NYRR race procedures and start page, and the warm-up structure and effects come from the recreational endurance runner warm-up study. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Race-morning protocol: waking, breakfast and pre-race preparation](/en/knowledge/race-morning-protocol/)
- [Race-day pacing: organising first and second half rhythm](/en/knowledge/race-day-pacing/)
- [Race checklist: gear and race-day checks](/en/tools/race-checklist/)
- [New York Marathon route profile and start procedure](/en/routes/new-york/)
- [Boston Marathon route profile and start arrangement](/en/routes/boston/)

## Sources and scope

Arrival advance, bag/toilet and corral-entry advice come from the official NYRR race procedures page. Wave and corral rules, corral open and close times, net timing, village toilets and bag inspection come from the official New York City Marathon start page. The running-plus-stretching warm-up structure, running economy and perceived-exertion results come from the 2021 recreational endurance runner warm-up study in the *International Journal of Environmental Research and Public Health*. The backward time chain, 10-minute arrival buffer, 90-minute wake prep, the 0–90 / 0–180 / 0–120 / 0–60 block caps and the warning wording are planning heuristics of this tool and are not in those official sources. Verified 2026-11-25. Not covered: that edition's shuttle times, security lanes and corral close times follow the race website handbook.

<!-- related-ring -->
## Related entries

- [Race qualifier checker: compare your result against the official standard, buffer and missing conditions](/en/tools/race-qualifier-checker/)
- [Pre-race taper plan: drop volume over two or three weeks, keep pace](/en/tools/taper-planner/)
- [Grade-adjusted pace — converting hill pace to flat-equivalent pace with the Minetti polynomial](/en/tools/grade-adjusted-pace/)
