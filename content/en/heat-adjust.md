---
entityId: tool:heat-adjust
locale: en
title: "Heat pace adjustment: estimate a slowdown from temperature and humidity"
summary: "Enter temperature, relative humidity, a cool-weather baseline pace and planned duration to estimate a heat-load band and an experience-based slowdown range. It is a practice-planning aid, not an official formula, and does not replace fluid planning, how you feel or medical advice."
aliases: ["Heat pace adjustment: estimate a slowdown from temperature and humidity", "heat pace adjustment"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What the tool is for

The same pace costs more in humid heat than in cool weather. This tool combines temperature and humidity into a simple heat score, maps it to a band, and returns an experience-based pace range.

It does not predict a finish time or tell you whether you are heat-acclimatised. Sun, wind, clothing, adaptation and hydration also matter. Effort can be judged with the talk test: at moderate intensity you can talk but not sing; at vigorous intensity you cannot say more than a few words without pausing for a breath.

## Formula and bands

- Heat score = temperature (°C) + 0.04 × relative humidity (%)

Each 25 points of humidity add one point. This is not a meteorological heat-index formula.

| Band | Score | Slowdown |
| --- | --- | --- |
| Cool | below 10 | 0% to 2% |
| Moderate | 10 to below 18 | 2% to 5% |
| Hot | 18 to below 24 | 5% to 8% |
| Very hot | 24 to below 30 | 7% to 10% |
| Extreme | 30 and above | 10% to 12% |

Adjusted pace low = baseline pace × (1 + low percentage); the high value uses the high percentage. The cut-offs and percentages are experience-based heuristics, not an official formula.

## Worked example

With 22 °C, 65% humidity, a 300 s/km baseline and 45 minutes planned:

| Item | Calculation | Result |
| --- | --- | --- |
| Heat score | 22 + 0.04 × 65 | 24.6 |
| Band | 24.6 is between 24 and below 30 | very hot |
| Pace low | 300 × 1.07 | 321 s/km |
| Pace high | 300 × 1.10 | 330 s/km |

At the boundary, 20 °C and 100% humidity give 24.0, exactly the lower edge of the very-hot band. At 240 s/km, the low value is 240 × 1.07 = 256.8, rounded to 257 seconds, and the high value is 264 seconds.

## Rounding and precision

The heat score keeps one decimal and paces round to whole seconds, so pace tolerance is 1 second; scores and percentages use 1e-6. Rounding happens only at the end, and a degree or a few humidity points can move the result across a boundary.

## How to read the result

The band suggests roughly how much to slow down, not a mandatory pace. Very hot or extreme bands are better used to postpone, shorten or move indoors. Aim for clear pale yellow urine during the day and drink more when active for long periods or in heat. Heavy sweating, weakness, dizziness, nausea, headache or fainting can indicate heat exhaustion: stop. Confusion, slurred speech, very high body temperature, a rapid pulse or loss of consciousness are emergencies: call emergency services first and cool the person while waiting.

## How to use it

1. Check the temperature and humidity, then enter a flat-weather baseline pace and the duration.
2. Read the heat score, band and adjusted pace range as a practice target.
3. Confirm fluids and cooling before starting; stop if heat-illness symptoms appear.

## Limits

The tool suits road, track and general outdoor running. It does not suit technical terrain or anyone already showing heat-illness symptoms, and it does not replace medical assessment. An extreme band is not permission to train slowly.

## When this number misleads you

The score is a simple monotonic weighting of temperature and humidity, not an official heat index. It uses the humidity you enter at that moment, while humidity changes during the race, and direct sun, still air and urban heat islands are not modelled. The baseline must be a flat, mild-weather aerobic pace; starting from an average that already includes hills or stops applies the slowdown to an already-wrong base. Taking the lower end of the range for a session longer than two hours usually understates heat load.

Do not use it to decide whether a race can go ahead, to diagnose heat illness, or in place of event medical rules and cancellation decisions. "Slow down by the band" is not permission to train; stop and seek help with dizziness, nausea or altered consciousness, and call emergency services when needed. This tool is not medical advice.

## Related reading

- [Heat and humidity: risk, acclimatisation and adjustment](https://learn.paobu.org/en/articles/heat-and-humidity/)
- [Hydration: how much and when](https://learn.paobu.org/en/articles/hydration/)

## Sources and scope

Heat-exhaustion signs (heavy sweating, weakness, dizziness, nausea, headache, fainting), heat-stroke emergency signs (confusion, slurred speech, very high body temperature, rapid pulse, possible loss of consciousness) and the call-first, cool-while-waiting instruction come from the U.S. National Weather Service. Clear pale yellow urine as a hydration guide, and more fluid in heat or during long activity, come from NHS guidance. The talk-test descriptions come from CDC guidance. The weights and ranges are experience-based heuristics. Verified 2026-11-06.
