---
entityId: knowledge:watch-gps
locale: en
title: "What watch heart rate and GPS can and cannot tell you"
summary: "A watch records estimated distance, pace and heart rate, not a certified course or a medical diagnosis. GPS drifts and optical heart rate lags, so readings only support decisions when they are checked against the same route, multi-week trends and perceived effort."
aliases: ["What watch heart rate and GPS can and cannot tell you", "Running watch data"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this page covers, and when it applies

This page covers the reliability limits of GPS distance, pace and heart rate data on running watches. It assumes the watch is used as a training aid, not a medical monitor; with cardiovascular symptoms, watch readings cannot replace a clinician's assessment. Technical notes on offline tracks and file structure are in [Track view](/en/tools/track-view/); when GPS signals are unreliable, backup navigation and trip planning follow U.S. National Park Service hiking safety guidance.

## GPS records a sampled track

The watch records latitude and longitude at intervals, connects adjacent points into a track, and estimates distance, elevation gain and pace from that geometry. Urban canyons, dense trees, ridgeline obstruction, tall buildings and reflective valleys can shift the recorded points; a GPX file stores track points, route points and elevation in an XML structure and does not automatically correct these errors. NPS hiking safety also notes that GPS signals can be unreliable, so a backup navigation method should be kept and the watch should not be relied on alone.

A common practical range is that open-country GPS drift sits around 1%-2%; when the same track shows error above 5%, signal or recording problems should be suspected before reading the result as running faster or slower. Shorter recording intervals keep denser points and more route detail, but can also record small drift segments; longer intervals make sharp turns look "straightened". These ranges are field experience references, not certified device specifications.

## Heart rate is an estimate too

Optical wrist sensors estimate heart rate from blood-flow changes and can lag or drop beats when the wrist moves randomly, arm swing is unstable or the band fits loosely. A small 2025 study compared a Fitbit Charge 4 against a Polar H10 chest strap: in stable running the optical sensor had a mean bias of 0.1 bpm and a mean absolute percentage error of 1.2% (SD 4.6%), with limits of agreement from −10.7 to 10.9 bpm; in orienteering, where wrist movement varied, error rose to 9.5% with a bias of −8.6 bpm. The authors do not recommend the device for settings needing high reliability and accuracy.

At review level, consumer wearables are not subject to the same regulatory accuracy requirements as medical devices; most included studies used Garmin watches, some with a chest-belt reference. Seven studies found devices valid or acceptable for VO2max estimation and three for lactate-threshold estimation, while the authors note usefulness in elite endurance sport as questionable. Watch-derived "training load", "recovery" or "lactate threshold" scores are algorithm estimates, not clinical measurements.

## Three cross-check rules

1. Compare weekly trends on the same route and in similar conditions; do not compare single sessions across different courses.
2. Match readings against perceived effort, breathing and leg feel; when they diverge clearly, suspect the device first.
3. Review the track file for unusually long straight segments, repeated backtracking and odd elevation gain before accepting the data.

The watch's main value is long-term recording and trends, not precise measurement of a single session. Logging methods are in [Training log](/en/knowledge/training-log/); when data look abnormal, start the check with route, weather and how you felt.

After a device upgrade or algorithm change, do not splice old and new readings onto one trend line: sensor position, sampling strategy and algorithm can all change, so segmented comparison is safer. The same watch also varies across seasons and paces; repeat an abnormal reading once or twice before deciding whether it is a device issue or a change in bodily state.

## Quick reference: when signals are more trustworthy

| Condition | GPS distance | Optical heart rate | Advice |
|---|---|---|---|
| Open road, started still | More reliable | Reliable with stable arm swing | Usable for trend comparison |
| Urban canyons, dense trees, ridgeline | More drift | Error grows with wrist movement | Read the rough range only |
| Hills, many turns, technical terrain | Distance easily straightened or inflated | Lag obvious with variable movement | Trust perceived effort |
| Loose band, slipping after sweat | Odd points | Jumping readings | Refit before recording |

## Worked example: how GPS drift changes average pace (hypothetical)

Assume the true distance is 5.00 km and time 31:00 (31.00 minutes), giving a true average pace of 31.00 ÷ 5.00 = 6.20 min/km, i.e. 6:12/km. If drift records 5.12 km at the same time, displayed pace is 31.00 ÷ 5.12 ≈ 6.05 min/km, about 6:03/km. Recording 0.12 km extra (2.4%) speeds the displayed pace by roughly 9 seconds per kilometre. Distance error converts directly into pace error, so judge pace from familiarity with the route and track shape, not the watch average alone.

## Worked example: recording interval and point spacing (hypothetical)

Assume pace is 12 km/h, or 12 ÷ 3.6 ≈ 3.33 m/s. At a 1-second interval adjacent recorded points are about 3.3 m apart; at 5 seconds they are about 16.7 m apart. On sharp turns the watch connects points with straight lines, cutting corners and underestimating distance; the more backtracking and weaving, the larger this straightening effect. The recording interval is a device setting and does not change the real route length.

## Common misconceptions

- Assuming watch pace is real pace. Pace comes from estimated distance divided by time, so distance drift flows straight into pace; course results are set by certified measurement.
- Treating a single heart-rate peak as a cardiac risk marker. Optical error rises in variable movement, and a jumping peak cannot support a diagnosis.
- Comparing pace across routes. Gradient, wind, surface and altitude change the physiological load at the same pace.
- Reading watch recovery or load scores as medical conclusions. These are algorithm estimates, and consumer devices are not held to medical-device accuracy rules.

## When to stop

An abnormal watch reading is not a reason to stop; chest pain, fainting, unusual palpitations, wheezing or breathlessness that does not settle at rest are. If these occur during exercise, stop and seek medical help rather than waiting for a watch alert. A resting heart rate 5 bpm or more above usual for a week points first to sleep, a cold, caffeine and training load; seek medical review if it persists.

## Frequency and progression

Every 4 weeks, compare the same route: whether pace, heart rate and perceived effort improve together. After a device upgrade or algorithm change, do not splice old and new data onto one trend line. Recording route, weather and shoe model explains changes better than a single pace number.

## Checklist

- Confirm enough satellites have locked before starting the record.
- Wear the band above the wrist bone and check it has not slipped after sweating.
- Review the raw file for unusually long straights or repeated backtracking.
- Compare week against week on the same route and time of day.
- Check watch data against breathing and leg feel; do not adjust training on readings alone.

## Scope and limits

This page does not diagnose, interpret an ECG or arrhythmia, or decide whether an episode was cardiac. The watch is not a certified medical monitor; people with chest pain, fainting, palpitations or cardiopulmonary disease should use clinically validated equipment and consult a clinician. Device specifications and error ranges follow the manufacturer's official documentation; the studies cited here have limited samples and do not generalize to every model.

## Related reading

- [Running form and force: efficiency, injury and individual rhythm](/en/knowledge/running-form/)
- [Route safety: solo running, weather and visibility](/en/knowledge/route-safety/)
- [Recovery and wearable data: metrics, trends and what they cannot answer](/en/knowledge/wearables-and-recovery-data/)
- [Training log: what to record and how to review it](/en/knowledge/training-log/)

## Sources and scope

The possibility of unreliable GPS and backup navigation follow the U.S. National Park Service hiking safety page; GPX file structure follows the TopoGrafix GPX 1.1 standard; the optical heart-rate contrast between stable running and variable movement follows a 2025 Fitbit-versus-chest-strap study; the regulatory position and validity status of consumer wearables follow a 2025 review. Study samples and models are limited and do not extend to every watch. Verified 2026-11-26.

<!-- related-ring -->
## Related entries

- [Achilles Pain — Two Types, Rehab Doses, and the Stop Signals](/en/knowledge/achilles-tendon-pain/)
- [Returning After an Ankle Sprain: Step Criteria, Step-Back Conditions, and Imaging Red Flags](/en/knowledge/ankle-sprain-and-return/)
- [Black toenails and nail problems — causes, prevention, and why not to drain them yourself](/en/knowledge/black-toenails/)
