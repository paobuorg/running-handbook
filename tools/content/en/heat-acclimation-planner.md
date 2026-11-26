---
entityId: tool:heat-acclimation-planner
locale: en
title: "Pre-race heat acclimation plan: estimate exposure shortfall and daily schedule from WBGT"
summary: "Enter the estimated race WBGT, arrival days, current daily heat exposure, planned acclimation days and daily session length. The tool estimates accumulated exposure, exposure shortfall and a low/moderate/high risk band, and produces a daily schedule that drops the last two sessions to 60%. WBGT combines temperature, humidity, wind and sun; the band is a planning threshold, not on-site cooling or medical judgement."
aliases: ["Pre-race heat acclimation plan", "heat acclimation planner", "heat adaptation schedule"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

Going to a hot race from a cool environment, the body needs time to build heat acclimation: sweat efficiency, plasma volume, heart-rate response and cooling rhythm improve gradually after repeated heat exposure, usually over one to two weeks. Arriving a few days early, how long you train in the heat each day, how much exposure you have already accumulated, and how much is left before the race decide whether you start adapted or just endure the heat. From estimated race-day WBGT, arrival days, current daily heat exposure, planned acclimation days and daily session length, this tool estimates accumulated exposure, exposure shortfall and a risk band, and lays out a daily schedule that cuts the last two sessions to 60%.

It suits runners travelling to a hot race who want to plan heat exposure by days and minutes. It does not suit four situations. First, you only have temperature and humidity, no WBGT conditions, and you enter temperature directly as WBGT. Second, race day may bring extreme heat; the risk thresholds do not replace an on-site cooling plan. Third, you have cardiovascular disease, a heat-illness history, or medication that affects heat dissipation; check a doctor first. Fourth, you read acclimation as "harder and longer is faster", ignoring recovery and fluid intake. The tool does not prescribe session intensity, fluid intake, cooling gear or medical monitoring.

## Inputs and units

WBGT is in degrees Celsius; days are integers; exposure and session length are in minutes.

| Input | Unit | Required | Notes |
| --- | --- | --- | --- |
| `raceWbgtC` | °C WBGT | Yes | Estimated race-day WBGT, range 10–40 |
| `arrivalDaysBefore` | days | Yes | Days arrived in the heat environment, 0–21 |
| `currentDailyHeatMinutes` | min | Yes | Current daily heat exposure, 0–240 |
| `planDays` | days | Yes | Planned acclimation days, 10–14 |
| `sessionMinutes` | min | Yes | Daily session length, 20–120 |

WBGT is wet bulb globe temperature, combining air temperature, humidity, wind speed and solar radiation. If only heat index or apparent temperature is available, it is a rough substitute: the heat index ignores wind and sun. Current daily heat exposure means training or activity minutes accumulated in the heat over recent days; sun during commuting does not count as training exposure.

## Formula, assumptions and rounding

The planner validates all five ranges first, then computes exposure and risk.

- Accumulated exposure = arrival days × current daily heat minutes.
- Planned exposure = plan days × session minutes.
- Shortfall = max(0, planned exposure − accumulated exposure).
- Risk band: high when WBGT ≥ 28 °C or shortfall > 300 min; otherwise moderate when WBGT ≥ 25 °C or shortfall > 120 min; otherwise low.
- Schedule: days 1 to the third-from-last keep sessionMinutes; the last two days are round(sessionMinutes × 0.6).

Rounding: schedule minutes round to the nearest whole minute; exposure totals and shortfall are whole minutes; band thresholds compare unrounded shortfall. Assumptions: WBGT is a pre-race estimate, and actual race-day temperature, humidity, wind and sun change it; accumulated exposure approximates arrival days times daily minutes without separating intensity, rest breaks or recovery; the 10–14 day plan follows the general workplace guidance that full acclimatization builds over one to two weeks of repeated exposure, with individual variation; the tool does not set session intensity, fluid intake, cooling equipment or on-site monitoring; the band is a planning threshold, not a clinical heat-illness classification.

## How to read the result

The result covers plan days, daily target, accumulated exposure, shortfall, risk band and the daily table.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Plan days / daily target | Days and single-session length of this plan | Schedule heat sessions per the table; taper the last two days |
| Accumulated exposure | Heat exposure minutes since arrival | A low value means weak acclimation base; allow more or steadier exposure |
| Shortfall | Planned exposure minus accumulated exposure | A larger shortfall means last-minute adaptation cannot be counted on |
| Risk band | Low / moderate / high | Moderate or high calls for extra cooling, fluid and start-time planning |
| Daily schedule | Minutes per day | The last two days drop to 60% to avoid carrying heat fatigue into the race |

Note that shortfall estimates time minutes only; a high-intensity session of the same minutes imposes far more heat stress than an easy walk. A zero shortfall means time coverage only, not full acclimation. On a high band, prioritize moving hard sessions earlier in the day, training in early morning or evening, and preparing ice towels and electrolytes rather than forcing midday exposure. Near or above 28 °C WBGT, cut single-session length and intensity further.

## Worked example one: typical

Race WBGT 26 °C, arrived 7 days early, current daily heat exposure 30 min, plan 14 days, daily session 45 min.

| Item | Calculation | Result |
| --- | --- | --- |
| Accumulated exposure | 7 × 30 | 210 min |
| Planned exposure | 14 × 45 | 630 min |
| Shortfall | 630 − 210 | 420 min |
| Risk band | Shortfall 420 > 300 | High |
| Schedule | First 12 days 45 min; last two 45 × 0.6 = 27 min | 12 × 45 + 2 × 27 |

WBGT 26 °C is below 28, but the shortfall exceeds 300 minutes, so the band is high. This case shows that even a moderate environment can push the band up when arrival is late and daily exposure has been small.

## Worked example two: boundary

Race WBGT 24 °C, arrived 14 days early, current daily heat exposure 45 min, plan 10 days, daily session 30 min.

| Item | Calculation | Result |
| --- | --- | --- |
| Accumulated exposure | 14 × 45 | 630 min |
| Planned exposure | 10 × 30 | 300 min |
| Shortfall | max(0, 300 − 630) | 0 min |
| Risk band | WBGT 24 < 25, shortfall 0 ≤ 120 | Low |
| Schedule | First 8 days 30 min; last two 30 × 0.6 = 18 min | 8 × 30 + 2 × 18 |

Accumulated exposure already exceeds planned exposure, so the shortfall is recorded as 0 and the band is low. This boundary matches a runner who arrived two weeks early and already has steady daily heat activity. Even on a low band, adjust start and fluid plan to the actual race-day WBGT.

## Worked example three: invalid or missing input

First invalid case: current daily heat exposure entered as 250 min. The upper bound is 240, so the planner rejects it as a range error on `currentMinutes` before exposure totals or a band are computed.

Second: WBGT entered as 8 or 42, outside 10–40, error field `wbgt`. Third: plan days entered as 8 or 15; only 10–14 are allowed, error field `planDays`. Fourth: session length entered as 15 or 130; the range is 20–120, error field `sessionMinutes`. Arrival days negative or above 21 raise an error on `arrivalDays`. Non-finite values are rejected as not-finite.

## Relationship to knowledge and routes

The NWS defines WBGT's components and how it differs from the heat index: WBGT combines temperature, humidity, wind speed and solar radiation, while the heat index combines only temperature and humidity and ignores wind and sun. OSHA heat-hazard guidance splits WBGT limits across light, moderate, heavy and very heavy workloads, and treats anyone on the job for less than one to two weeks as unacclimatized, with acclimatization built through repeated heat exposure. The ACSM 2021 expert consensus groups recognition, management and prevention of exertional heat illness, noting that risk comes from exercise intensity, environmental heat load and individual susceptibility combined; suspected heat stroke means stop exercise, cool aggressively and call emergency care. These readings connect to [heat and humidity](/en/knowledge/heat-and-humidity/).

Fluid and electrolyte arrangement is covered in [hydration](/en/knowledge/hydration/), race-day pace adjustment in [heat-adjust](/en/tools/heat-adjust/), sweat and electrolyte estimation in the [sweat-rate calculator](/en/tools/sweat-rate/), and sun protection in [sun and UV exposure](/en/knowledge/sun-and-uv-exposure/).

## Common failure modes and early signals

The first failure mode is looking at temperature only and ignoring humidity and wind. At 28 °C with high humidity and no wind, cooling is poor and WBGT is noticeably higher than the apparent feel. Early signal: heart rate climbs fast in humid, still training sessions.

The second is compressing acclimation into the last two or three days. The body needs repeated exposure; one long sun blast before the race adds heat fatigue instead. Early signal: a long hard session on arrival day, followed by worse sleep and recovery that evening.

The third is skipping the final taper. Still running peak-length sessions at the end of acclimation carries heat fatigue into race day. Early signal: unusually heavy sweating or a high morning pulse in the last two days.

The fourth is treating the band as a safety certificate. A low band only means modest pressure under the time and environment estimate; trail sun exposure, climbs and sparse aid stations can still change heat load on race day. Early signal: an exposed course with little shade and few aid stops.

## Limits

This tool plans heat-exposure days and minutes before a race, for running and trail race preparation. It does not judge heat illness during the race, diagnose illness, or prescribe specific session intensity, fluid plan, cooling gear or medical monitoring. People with cardiovascular disease, a heat history, uncorrected dehydration, pregnancy, or medication affecting heat dissipation should consult a doctor first. Measured on-site WBGT, course shade and wind, personal sweat rate and electrolyte needs are judged on race day against actual conditions.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, and the risk framing draws on the ACSM 2021 heat-illness consensus, OSHA heat-hazard guidance and the NWS WBGT explanation. No existing knowledge body was rewritten in this round.

## Related reading

- [Heat and humidity: factors in running heat stress](/en/knowledge/heat-and-humidity/)
- [Hydration: fluid and electrolyte intake plan](/en/knowledge/hydration/)
- [Heat-adjust: pace and fluid advice in hot conditions](/en/tools/heat-adjust/)
- [Sweat-rate calculator: fluid replacement from weight change](/en/tools/sweat-rate/)
- [Sun and UV exposure: safe hours and protection](/en/knowledge/sun-and-uv-exposure/)

## Sources and scope

The overall recognition, management and prevention framework comes from the ACSM 2021 expert consensus (PubMed 34524191). The four WBGT factors, workload-tiered limits, one-to-two-week acclimatization window and the heat-index substitution limitation come from the OSHA heat-hazards guidance. The three-temperature WBGT definition, the difference from the heat index and its use come from the U.S. National Weather Service WBGT page. The 25/28 °C tiers, 120/300 minute shortfall thresholds and the 60% final-two-day taper are planning heuristics of this tool and do not appear verbatim in those official sources. Verified 2026-11-25. Not covered: measured course WBGT, personal sweat rate and heat-illness history require on-site and individual assessment.

<!-- related-ring -->
## Related entries

- [Shoe mileage log: track training-shoe distance locally](/en/tools/shoe-mileage/)
- [Sweat-rate estimate — using pre- and post-run body mass and fluid intake](/en/tools/sweat-rate/)
- [Running pain self-check: seven questions before deciding on assessment](/en/tools/injury-risk-check/)
