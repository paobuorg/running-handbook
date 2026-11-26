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

The same pace costs more in humid heat than in cool weather. This tool combines temperature and humidity into a simple heat score, maps it to a band, and returns an experience-based pace range, helping you set a realistic practice goal before you leave home. It suits daily training, easy long runs and pre-race pace plans, and a weekly re-check during a heat spell.

It does not predict a finish time or tell you whether you are heat-acclimatised. Sun, wind, clothing, adaptation and hydration also matter. Effort can be judged with the talk test: at moderate intensity you can talk but not sing; at vigorous intensity you cannot say more than a few words without pausing for a breath.

## Inputs and outputs

There are four inputs: temperature (°C), relative humidity (%), a flat mild-weather baseline pace (seconds per kilometre) and planned duration (minutes). Outputs are the heat score, the adjusted pace low and high, the heat band and a plain-language note with stop signals. The score indicates roughly which heat category the conditions fall into; the pace range indicates how much slower the baseline pace should roughly become at that level. Duration is exposure context only: longer sessions lean toward the upper end with extra caution, but it does not change the percentages directly.

## Formula and bands

The heat score uses a simple monotonic weighted sum:

- Heat score = temperature (°C) + 0.04 × relative humidity (%)

Each 25 points of humidity add one point. This weight keeps humid conditions at the same temperature on a higher heat load; it is not a meteorological heat-index formula.

| Band | Score | Slowdown |
| --- | --- | --- |
| Cool | below 10 | 0% to 2% |
| Moderate | 10 to below 18 | 2% to 5% |
| Hot | 18 to below 24 | 5% to 8% |
| Very hot | 24 to below 30 | 7% to 10% |
| Extreme | 30 and above | 10% to 12% |

Adjusted pace low = baseline pace × (1 + low percentage); the high value uses the high percentage. The cut-offs and percentages are experience-based heuristics, not an official formula or a prediction of individual performance.

## Worked example 1: very-hot band

With 22 °C, 65% humidity, a 300 s/km baseline and 45 minutes planned:

| Item | Calculation | Result |
| --- | --- | --- |
| Heat score | 22 + 0.04 × 65 | 24.6 |
| Band | 24.6 is between 24 and below 30 | very hot |
| Pace low | 300 × 1.07 | 321 s/km |
| Pace high | 300 × 1.10 | 330 s/km |

This example suggests slowing the baseline pace by about 7% to 10% in humid but not extreme conditions. The figures follow independent arithmetic, not the page script; the pace conversion changes numbers only and does not guarantee the session can be held at that pace.

## Worked example 2: the 24.0 lower boundary

At the boundary, 20 °C and 100% humidity give 20 + 0.04 × 100 = 24.0, exactly the lower edge of the very-hot band. At a 240 s/km baseline, the low value is 240 × 1.07 = 256.8, rounded to 257 seconds, and the high value is 240 × 1.10 = 264 seconds. Boundary values are inclusive: 24.0 belongs to very hot rather than hot. This case checks cut-off membership and rounding direction.

## Worked example 3: extreme band

With 32 °C, 70% humidity, a 300 s/km baseline and 120 minutes planned: heat score = 32 + 0.04 × 70 = 34.8, in the extreme band (30 and above). The slowdown range is 10% to 12%: low 300 × 1.10 = 330 s/km, high 300 × 1.12 = 336 s/km. The 120-minute duration is a long exposure, so lean toward the upper end with extra caution. The extreme band does not mean "train slowly and keep going"; postponing, shortening or moving indoors is the safer choice.

## Rounding and precision

The heat score keeps one decimal and paces round to whole seconds, so pace tolerance is 1 second; scores and percentages use 1e-6. Rounding happens only at the end, so a rounded figure is not multiplied again. Input temperature and humidity usually come from a forecast or watch and are imprecise; one degree or a few humidity points can move the result across a boundary. When recomputing by hand, keep the unrounded product before rounding to seconds.

## Reading the result

The band suggests roughly how much to slow down, not a mandatory pace. Very hot or extreme bands are better used to postpone, shorten or move indoors rather than to force a slower target. Aim for clear pale yellow urine during the day and drink more when active for long periods or in heat. Heavy sweating, weakness, dizziness, nausea, headache or fainting can indicate heat exhaustion: stop. Confusion, slurred speech, very high body temperature, a rapid pulse or loss of consciousness are emergencies: call emergency services first and cool the person while waiting.

## Common pitfalls

The first pitfall is treating the heat score as an official heat index: it is a temperature-and-humidity weighted sum with no sun, wind, clothing or adaptation terms. The second is a wrong baseline: an average that already includes hills, stops or fatigue applies the slowdown to an already-slow base. The third is taking only the lower end of the range for a session over two hours, which usually understates heat load. The fourth is reading the band as permission to train; in extreme conditions, slowing down is not a reason to push on.

## Limits

The tool suits road, track and general outdoor running. It does not suit technical terrain or anyone already showing heat-illness symptoms, and it does not replace medical assessment, event medical rules or on-site cancellation decisions. An extreme band is not permission to train slowly. Below −20 °C or above 50 °C, and outside 0–100% humidity, no calculation is produced. The baseline must be a flat, mild-weather aerobic pace; hills, altitude, direct sun and strong wind need separate adjustment. With altered consciousness, fainting or persistent discomfort, stop and seek help; in an emergency call first.

## How to use it

1. Check the temperature and humidity, then enter a flat-weather baseline pace and the duration.
2. Read the heat score, band and adjusted pace range as a practice target.
3. Confirm fluids and cooling before starting; stop if heat-illness symptoms appear.

## Related reading

- [Heat and humidity: risk, acclimatisation and adjustment](/en/knowledge/heat-and-humidity/)
- [Hydration: how much and when](/en/knowledge/hydration/)
- [Race-day fuelling: carbohydrate, fluid and rhythm](/en/knowledge/race-day-fueling/)
- [Electrolytes and sodium: sweat loss and replacement](/en/knowledge/electrolytes-and-sodium/)

## Privacy and data

Inputs are computed locally and not uploaded or saved. Forecast data comes from your own source; the tool reads no location, watch health data or personal identity. Close the page on a shared device.

## Sources and scope

Heat-exhaustion signs (heavy sweating, weakness, dizziness, nausea, headache, fainting), heat-stroke emergency signs (confusion, slurred speech, very high body temperature, rapid pulse, possible loss of consciousness) and the call-first, cool-while-waiting instruction come from the U.S. National Weather Service. Clear pale yellow urine as a hydration guide, and more fluid in heat or during long activity, come from NHS guidance. The talk-test descriptions come from CDC guidance. The weights, cut-offs and 0% to 12% slowdown ranges are experience-based heuristics not found in those sources. Verified 2026-11-26.

<!-- related-ring -->
## Related entries

- [Pace calculator: distance, time, pace and speed](/en/tools/pace/)
- [Race-time estimate: the Riegel formula with a 1.06 exponent](/en/tools/race-predict/)
- [Result split analyzer: first/second-half fade, fade point and target gap](/en/tools/result-split-analyzer/)
