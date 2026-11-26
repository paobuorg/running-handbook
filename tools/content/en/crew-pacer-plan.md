---
entityId: tool:crew-pacer-plan
locale: en
title: "Crew and pacer plan: schedule handoffs against the official access list"
summary: "Enter the course distance, start and target finish, and each access point's km, name, crew flag and pacer flag. Under an even-pace assumption the tool projects arrival and crew call times, lists pacer legs, the longest crew gap, and points with neither access nor a pacer change. Access rights follow the official race rules."
aliases: ["Crew and pacer plan", "crew pacer plan", "aid-station handoff schedule"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

Crewing a long trail race is not simply driving to aid stations and waiting. Which stations crews may enter, which are restricted to official vehicles, where a pacer may start and hand off, how early crew must arrive, and how long a runner goes without supplies or a change of person between access points all have to be arranged before the race against the official access list. This tool places that list next to your target finish, projects an arrival clock and a crew call clock at each handoff stop under an even-pace assumption, lists consecutive pacer legs and the longest crew gap, and flags points that open to neither crew nor a pacer change.

It suits runners who already have the official station access list and need to arrange crew or pacers, and leads who want to check supplies, transport and handoff rhythm. It does not suit three situations. First, when the race does not allow crew or pacers at all; any handoff the tool schedules then has no rule basis. Second, when you do not yet know each station's access status and guess the crew and pacer flags. Third, when a projected arrival is treated as a committed time and crew waits by the clock rigidly. The even-pace projection is a scheduling aid only, not a substitute for on-site access rules, parking arrangements or medical judgement.

## Inputs and units

Clock inputs are 24-hour `HH:MM`, converted to minutes since midnight internally. Distance is in kilometres; crew lead time is in minutes; arrival and call clocks display whole minutes.

| Input | Unit | Required | Notes |
| --- | --- | --- | --- |
| `distanceKm` | km | Yes | Course distance, greater than zero |
| `startClock` | HH:MM | Yes | Start time |
| `targetFinish` | HH:MM | Yes | Target finish clock; later than the start |
| `accessPoints` | rows | Yes | One row: `km,name,crew,pacer`; crew/pacer are 1 or 0; km strictly increasing |
| `crewLeadMinutes` | min | No | Crew lead time, default 20, range 0–120 |

One station per line, for example `55.7,Michigan Bluff,1,1` means crew access and a pacer change at 55.7 km; `85.2,Auburn Lake Trails,0,0` means neither. Keep station names as written in the official table so crew can communicate by name.

## Formula, assumptions and rounding

The planner first checks that the start precedes the target finish, then computes an even pace from the target duration: pace (km per minute) = distanceKm ÷ (target finish − start).

- Predicted arrival = start + km ÷ pace.
- Crew call clock = predicted arrival − crew lead minutes.
- Crew-access points are ordered by arrival; adjacent arrival differences are crew gaps, and the longest gap is the maximum.
- Pacer points are paired consecutively into pacer legs, with leg km equal to the distance between the two stations.
- A point with crew true or pacer true enters the handoff list; a point with both false appears only in warnings.

Warning rules: a crew gap above 120 minutes triggers a staffing and supply check; a single crew point warns that gaps cannot be checked; a neither-crew-nor-pacer point is listed separately. The 120-minute threshold is a scheduling heuristic, not a race rule.

Rounding: arrival and call clocks round to the nearest whole minute; crew gaps and the longest gap round to the nearest whole minute; pacer leg km keep two decimals. Key assumptions: pace is even across the race, with no model for climbs, stops or fatigue; all clocks fall on the same day; access status follows the official list you entered, and the tool does not verify current regulations; the plan covers where to hand off and when to arrive, not supply transport, driving routes or on-site communication.

## How to read the result

The result has four parts: the handoff table, the pacer-leg table, the longest crew gap, and the warnings.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Handoff stops | Predicted arrival and crew call clock at each accessible station | Crew leaves early enough for the call clock; the runner prepares for the handoff at arrival |
| Pacer legs | Segments between consecutive pacer-change stations and their distance | Assign pacers to legs and make clear who runs which segment |
| Longest crew gap | Longest wait between adjacent crew stops | Carry supplies, clothing and transport plans across long gaps |
| Warnings | Non-access points, over-long gaps, single-point gap check | Confirm each item before the race; do not write warning stations into the handoff plan |

Note that predicted arrivals are even-pace back-calculations; real arrivals slip later because of climbs, queues and fatigue, and the crew call clock should keep extra margin on top of the lead minutes. Pacer legs mark handoff positions only; a pacer may not join the trail anywhere between stations. Most races require the pacer to run the whole leg to the next access station. When the longest crew gap exceeds 120 minutes, check fluid, clothing changes and rotation across that stretch.

## Worked example one: typical

Course 100 km, start 05:00, target finish 17:00, crew lead 20 minutes; five of six stations open to crew, three open to pacer changes, the last opens to neither.

| Station | km | Arrival | Crew call |
| --- | --- | --- | --- |
| Duncan Canyon | 24.4 | 07:56 | 07:36 |
| Robinson Flat | 30.3 | 08:38 | 08:18 |
| Michigan Bluff | 55.7 | 11:41 | 11:21 |
| Foresthill | 62 | 12:26 | 12:06 |
| Rucky Chucky | 78 | 14:22 | 14:02 |

Target duration is 720 minutes; pace is 100 ÷ 720 km per minute, or 7.2 min per km. Crew gaps are 42.48, 182.88, 45.36 and 115.2 minutes; the longest is 182.88, rounded to 183 minutes, between Robinson Flat and Michigan Bluff. Pacer legs are Michigan Bluff to Foresthill, 6.3 km, and Foresthill to Rucky Chucky, 16 km. Auburn Lake Trails opens to neither, so it appears only in a warning; the 183-minute crew gap also triggers the long-gap warning.

## Worked example two: boundary

Course 21.1 km, start 08:00, target finish 09:30, crew lead 0 minutes; one station, Midpoint at 10.5 km, open to both crew and pacer.

| Item | Calculation | Result |
| --- | --- | --- |
| Arrival | 480 + 10.5 × 90 ÷ 21.1 = 524.787 | 08:45 |
| Crew call | Arrival − 0 min | 08:45 |
| Pacer legs | One pacer point only | None |
| Longest crew gap | One crew point only | 0 min |

With a single point there are no adjacent gaps to compare, so the longest gap is 0 and a warning notes that gaps cannot be checked. This boundary matches a short race or a pacer joining only near the finish.

## Worked example three: invalid or missing input

First invalid case: an empty access-point list. The rules require at least one point, otherwise no handoffs, legs or gaps can be produced; the planner throws a range error on `accessPoints`.

Second: a station km beyond the course, or two rows whose km values are not strictly increasing, is rejected as a range error. Third: a row such as `55.7,Michigan Bluff,1` missing a column, or a crew/pacer value outside 1/0, fails parsing on the client with a line-numbered format error. Fourth: a target finish earlier than the start raises an order error on `targetFinish`. Crew lead minutes outside 0–120 raise an error on `crewLead`.

## Relationship to routes and knowledge

Access rules differ sharply between races. UTMB regulations allow one Personal Assistant at designated aid stations, who must meet the runner there and leave after it; no assistance is authorised outside the designated zones. The Western States 100 chart marks crew access and pacer change columns station by station, and pacers join only at designated change stations. Hardrock 100 allows pacers from Grouse Gulch onward, limits the runner to one pacer at a time, requires the pacer to run the whole leg to the next crew-access station, and mandates check-in, a signed waiver and a wristband; crew activity stays within roughly a 400-yard radius of the station. These rules are recorded in the [UTMB](/en/routes/utmb/) and [Western States 100](/en/routes/western-states/) route profiles.

Race-day rhythm is covered in [race-day pacing](/en/knowledge/race-day-pacing/), carried and handoff gear in [trail gear](/en/knowledge/trail-gear/), and pre-race checks in the [race checklist](/en/tools/race-checklist/).

## Common failure modes and early signals

The first failure mode is guessing access rights from memory. A station may look close to a road yet be restricted to official vehicles. Early signal: a station you marked crew=1 shows No in the official crew-access column.

The second is writing the wrong pacer-change station. A pacer cannot join at any roadside; check-in happens at designated change stations. Early signal: the planned pacer start is not on the official pacer-change column.

The third is underestimating crew gaps. Three or four hours between access points mean the runner carries food, fluid and clothing. Early signal: the longest crew gap exceeds 120 minutes with no matching self-supply plan.

The fourth is treating projected arrivals as committed times. Climbs, queues and night running push arrival later than the even projection. Early signal: crew arrives 20 minutes before the projected call clock only to find the runner still on the previous climb.

## Limits

The tool suits pre-race scheduling for trail races and long road races completed within one day and backed by an official station access list. It does not handle after-midnight arrival, and it does not model altitude, climbs, surface, heat, wind, parking queues or night fatigue, nor does it verify that season's access eligibility. Pacer age limits, check-in, waiver and wristband requirements follow the race regulations; the tool gives no medical or transport advice. If rules change or a station closes temporarily, follow the on-site announcement.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, and the access wording comes from the UTMB regulations, the Western States 100 station chart and the Hardrock 100 official pacer and crew page. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Race-day pacing: first and second half rhythm and split targets](/en/knowledge/race-day-pacing/)
- [Trail gear: carried and handoff supplies](/en/knowledge/trail-gear/)
- [Race checklist: gear and race-day checks](/en/tools/race-checklist/)
- [UTMB route profile and personal assistant rules](/en/routes/utmb/)
- [Western States 100 route profile and station access chart](/en/routes/western-states/)

## Sources and scope

The meeting and departure station requirements for a personal assistant and the restriction on assistance outside designated zones come from the official UTMB World Series regulations. The crew-access and pacer-change columns and station parking restrictions come from the official Western States 100 aid-station page. The pacer start station, one-pacer limit, whole-leg requirement, check-in/waiver/wristband and 400-yard crew radius come from the official Hardrock 100 pacer and crew rules page. The 120-minute long-gap threshold, even-pace arrival projection and scheduling arithmetic are planning heuristics of this tool and are not in those official sources. Verified 2026-11-25. Not covered: that season's pacer roster, transport permits and parking arrangements follow the race website's current announcement.

<!-- related-ring -->
## Related entries

- [Cutoff buffer planner: check each checkpoint against the official cutoff table](/en/tools/cutoff-planner/)
- [Race checklist: generated by surface, duration and weather](/en/tools/race-checklist/)
- [Race-day timeline planner: work backward from the gun to wake-up and every reserve](/en/tools/race-day-timeline/)
