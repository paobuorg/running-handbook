---
entityId: tool:course-recon-checklist
locale: en
title: "Course recon checklist generator — what to check by distance, night, crew and GPX"
summary: "Enter distance, gain, duration, technicality, night, crew and GPX to get a categorised checklist, high-priority count, desktop minutes, field runs and risk band."
aliases: ["赛道侦察清单", "course recon checklist", "赛道勘察", "recon checklist"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

Course recon usually fails not because nobody looked at the map, but because looking never became a checklist. This tool uses distance, gain, race hours, technicality, night sections, crew access and GPX availability to generate a categorised recon checklist, plus desktop minutes, field recon runs and planning complexity.

It does not judge whether the course is hard, and it does not replace the official rules. It answers “what must be confirmed before the start, and in what order”.

## Inputs and outputs

Seven inputs: distance (km), elevation gain (m), expected race duration (hours), technicality (low/medium/high), night section, crew access and official GPX availability. Outputs are item count, high-priority count, desktop minutes, field recon runs, risk band and the checklist.

Each row has a category, item and priority. Categories cover rules, course, aid, navigation, bailout, weather, gear, crew and race execution.

## Rules and formula

```
13 base items: rules 3, course 2, aid 2, nav 3, bailout 1, weather 1, race 1
technicality ≥ medium: + surface and terrain notes
technicality high: + field recon run
night: + sunrise/sunset, night kit
crew: + crew access, pacer handoffs, drop bags
no GPX: + paper map
gain/distance > 30 m/km: + poles
desktopMinutes = round(45 + 0.5×distance + 0.02×gain + tech add + 20 if night + 15 if crew)
field runs = 3 high / 2 medium / 1 low
```

Tech add is 30 minutes for high, 15 for medium, 0 for low. Desktop minutes are a planning estimate, not a promise.

## Input ranges

| Input | Range | Meaning |
|---|---|---|
| Distance | 1–500 km | desktop minutes and gain ratio |
| Gain | 0–30000 m | gain ratio and poles |
| Duration | 1–60 h | risk band |
| Technicality | low/medium/high | terrain and field recon |
| Night | yes/no | lighting and sunrise/sunset |
| Crew | yes/no | crew items |
| GPX | yes/no | paper map when absent |

Out-of-range values fail; negative gain fails too.

## Case one: 42 km road marathon, 800 m gain

| Item | Result |
|---|---|
| Items | 17 |
| High priority | 14 |
| Desktop minutes | 112 |
| Field runs | 2 |
| Risk | moderate |

Medium technicality adds surface notes; crew adds crew access, pacer handoffs and drop bags; no night section means no lighting items. 112 minutes is roughly two afternoon sessions.

## Cases two and three

| Scenario | Items | High | Desktop | Field | Risk |
|---|---|---|---|---|---|
| 100 km, 6000 m gain, 24 h, high tech, night, crew, no GPX | 22 | 18 | 280 | 3 | high |
| half marathon, 200 m gain, 2 h, low tech, no night, no crew, GPX | 13 | 11 | 60 | 1 | low |

The 100 km row triggers almost every add-on: night, technical terrain, crew, no GPX and 60 m/km gain, so it has the longest list and the most desktop time. The half marathon keeps the 13 base items.

## How to read the risk band

| Band | Trigger | Suggestion |
|---|---|---|
| High | night / high technicality / ≥12 h | at least 3 field visits, start 8 weeks out |
| Moderate | medium technicality / ≥6 h | 2 field visits, 4–6 weeks out |
| Low | otherwise | 1 field visit, 2–4 weeks out |

The band describes planning complexity, not personal safety. Weather, health and rescue capability are separate.

## How to use priority

Do high-priority items first: rules, mandatory gear, cut-offs, course map, elevation profile, aid stations, water, GPX, waypoints, offline map, escape routes. If any is missing, do not start field recon.

Medium items (historical weather, pace card, drop bags, poles) can wait until after field recon. A longer list is not better; doing medium items before high ones is fake productivity.

## GPX versus no GPX

With official GPX: import it, check start/finish and waypoints, build an offline map, mark escape points. Without GPX: find the official static map or course description, build a paper map and waypoint table, then decide whether to use someone else’s track (check licence and accuracy).

Do not treat an uploaded track as official geometry; route pages state geometry source and licence, so read them first.

## Chinese runners

Chinese trail checkpoints are often in small villages with patchy signal. Download offline maps and write checkpoint names and kilometres on a paper card; for night sections carry a primary torch, a spare torch and batteries, not just a phone light.

For overseas races, check whether the GPX includes checkpoint waypoints and whether the course changes each year; an old GPX is a reference, not navigation.

## Common mistakes

One: studying the map but not the rules and mandatory gear. Two: having a GPX and skipping the offline map. Three: downloading any track when there is no official GPX. Four: only one torch for a night section. Five: crew access without handoff times.

Six: treating the risk band as personal safety. Seven: a long list with high-priority items unfinished. Eight: one field run without checking escape routes.

## Checklist

Desktop: rules, gear, cut-offs, map, profile, aid, water, GPX, waypoints, offline map, escape. Field: start/finish, key turns, checkpoints, night entry, escape routes, crew parking.

Update after each recon: cross off confirmed items and add what you found. The checklist is alive, not a one-off.

## Related reading and tools

Read [GPX course recon](/en/knowledge/gpx-course-recon/) for the six-step flow; use [route elevation](/en/tools/route-elevation/) for the profile; use the [cut-off planner](/en/tools/cutoff-planner/) for checkpoint timing.

Route pages link official GPX or static maps and state geometry licence; read them before downloading.

## Recon timeline

Eight weeks out: read rules, mandatory gear, cut-offs, course map and profile; build the first checklist. Six weeks: import GPX, build the offline map, mark waypoints and escape points. Four weeks: first field visit, focused on start/finish, key turns, checkpoints and night entry. Two weeks: second visit, walk escape routes and crew parking. One week: review only, no plan changes.

Earlier is not always better; a course may still be under construction or re-routed. Write new findings back into the checklist and review only the changes next time.

## What can be removed

Longer is not better. For a city road race, daylight, no crew and a complete official GPX, drop night kit, pacer handoffs, drop bags and poles; keep rules, cut-offs, aid, navigation, escape and weather.

For high altitude, night, technical terrain and no GPX, remove no high-priority item; only decorative medium items can go, never safety items. Every removal needs a reason, not a prettier list.

## How to record in the field

At each key point take three photos: sign/turn, checkpoint entrance, escape-route entrance; name them “km-name-direction”. Back at the hotel, match photos to GPX waypoints and mark where reality differs from the map.

Do not write “hard” or “slippery”; write “200 m after the right turn at km 38, loose downhill, take the inside line when wet”. Specific notes are reusable next recon or on race day.

## Sources and verification boundary

The checklist structure draws on public UTMB and Western States course/GPX pages and this site’s editorial method; sources and claims are in the entity JSON. It is not the official mandatory-gear list and does not replace the race briefing.

Last verified: 2026-11-26. Next review trigger: race-rule changes, GPX standards, course re-routes.
