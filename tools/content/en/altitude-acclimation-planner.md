---
entityId: tool:altitude-acclimation-planner
locale: en
title: "Altitude acclimation planner: arrival and staging schedule by race altitude"
summary: "Enter race altitude, race date, arrival lead and current altitude to get recommended lead time, staging altitude, risk band and a day-by-day schedule. Planning only; not a substitute for a clinician or race medical team."
aliases: []
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

“How many days before altitude” usually gets two extremes: one day or two weeks. This tool puts race altitude, current altitude and arrival lead into one table so you can see the recommended lead, staging altitude and risk band instead of guessing at booking.

It is planning only; it does not diagnose altitude illness or replace a clinician. Resting breathlessness, altered consciousness or inability to walk is an emergency.

## Inputs and outputs

Five inputs: race altitude (0–5,000 m), race date (YYYY-MM-DD), arrival days before (0–30), current altitude (default 0), and race date. Outputs: recommended lead, staging altitude, risk band, day-by-day schedule and warnings.

The schedule lists key arrival and altitude nodes, not hourly training; volume, intensity and rest after arrival remain your and your coach's decision.

## Formula and rounding

```
Recommended lead = 1 (≤1,500 m)
                 = 2 (1,500–2,500 m)
                 = 7 (2,500–3,500 m)
                 = 10 (>3,500 m)
Staging altitude = min(3,000, round(race altitude × 0.65 / 100) × 100)
Risk band = low (arrival ≥ recommendation)
          = moderate (arrival ≥ 50% of recommendation)
          = high (arrival < 50% of recommendation)
```

Days are integers; staging altitude rounds to 100 m and caps at 3,000 m. The formula is a planning heuristic, not a physiological model.

## Why it is not a prescription

Responses to the same altitude vary widely; sleep, dehydration, illness, age and previous altitude history all change risk. The table helps schedule time; it cannot predict whether you will develop altitude illness. Worsening headache, resting breathlessness, cough, altered consciousness or inability to walk means descent and help outrank any schedule.

## How to read the risk band

| Band | Meaning | Action |
| --- | --- | --- |
| Low | Arrival meets recommendation | Still hydrate, start slow, monitor sleep |
| Moderate | About half the recommendation | Treat the race as an adaptation day, not a PB |
| High | Clearly insufficient | Consider changing travel; keep 24–48 h |

The band is not a “go/no-go” verdict; it is a prompt to adjust the itinerary.

## Example 1: 2,300 m half, 3 days early

| Item | Result |
| --- | --- |
| Recommended lead | 2 days |
| Staging altitude | 1,500 m |
| Risk band | Low |
| Schedule | 1,500 m on arrival → 2,300 m two days before → race |

Three days exceeds the recommendation, so risk is low; still walk only on day one, hydrate, sleep early and do not chase pace in the first 5 km.

## Example 2: 3,500 m 50K, 2 days early

| Item | Result |
| --- | --- |
| Recommended lead | 7 days |
| Staging altitude | 2,300 m |
| Risk band | High |
| Schedule | 2,300 m on arrival → 3,500 m next day → race |

Two days is high risk. The tool will not cancel the race for you, but it states clearly: change the goal from “chase a time” to “finish and stay safe”, hydrate and monitor breathing and consciousness.

## Example 3: 4,200 m 100K, 12 days early

| Item | Result |
| --- | --- |
| Recommended lead | 10 days |
| Staging altitude | 2,700 m |
| Risk band | Low |
| Schedule | 2,700 m for 6 days → 4,200 m for 4 days → race |

Twelve days meets the recommendation, so risk is low; 4,200 m can still produce HAPE/HACE. Keep the last three days to easy walking; on race day downgrade by breathing and gait.

## How to use the schedule

Treat it as arrival and altitude nodes, not a training plan. Reduce intensity and protect sleep for two days before travel; walk only, hydrate and eat normally for 24–48 hours after arrival; at race altitude, walk easily and monitor morning heart rate, headache, urine and gait. Any abnormality means stop, not add training.

## Who should not use it

- Diagnosed heart/lung disease, uncontrolled hypertension or severe anaemia: consult a clinician first.
- Race altitude above 5,000 m or routes requiring expedition medical support.
- Acute altitude illness: output cannot replace descent and treatment.
- Infants, pregnant people or special populations: not applicable.

## Common errors

- Treating “recommended lead” as mandatory and ignoring individual variation.
- Adding training after early arrival and arriving more fatigued.
- Masking headache with painkillers and continuing to ascend.
- Looking only at altitude, not sleep, dehydration or illness.
- Setting staging altitude above the race altitude.
- Racing on schedule despite HAPE/HACE symptoms.

## Three things beyond the schedule

First, sleep. Altitude sleep is often worse than at sea level, with frequent waking from lower oxygen; do not schedule early training after arrival, protect 7–8 hours in bed. Second, fluid and food. Altitude diuresis and breathing water loss raise dehydration risk; sip fluids, eat normal carbohydrate and protein, do not rely on energy drinks. Third, intensity. For 48 hours after arrival, walk only; no long run or strength in the last 24 hours. Treat adaptation as part of training, not wasted time.

## Race-day altitude checklist

| Time | Action | Check |
| --- | --- | --- |
| 48 h before | Arrive, hydrate, sleep early | Headache, urine, sleep |
| 24 h before | Easy walk 20–30 min | Resting breathing, gait |
| 1 h before | Normal breakfast, small fluid | Not empty, not full |
| Start | First 5 km 10–15% slower | Breathing, heart rate |
| During | Assess consciousness and cough every 2 h | Breathlessness, pink sputum |
| Finish | Warm, hydrate, descend | Do not stay high |

This checklist does not replace race medical care; HAPE/HACE symptoms mean descent and help first.

## Why staging is 65%

Sixty-five percent is a conservative planning ratio: low enough to be clearly below race altitude, high enough to find lodging within reasonable travel. It does not guarantee adaptation; it creates an intermediate step and reduces the size of a single ascent. If the race is 3,000 m and staging is only 1,500 m, the jump is still large; if staging is near race altitude, the staging purpose disappears.

In practice, prioritise travel time from staging to the race, refundable lodging and access to medical care. Altitude is not the only criterion.

## Training after arrival

| After arrival | Training | Purpose |
| --- | --- | --- |
| Day 1 | Walk 20–30 min | Observe response |
| Day 2 | Easy walk/very slow jog 30 min | Keep circulation |
| Days 3–4 | Easy 30–40 min | Adaptation |
| 2 days out | Walk + mobility only | Save energy |
| 1 day out | Rest/walk 15 min | Sleep first |

Do not add “acclimation training”; altitude load is already higher than sea level, and extra work only adds fatigue and risk.

## Three failure cases

**Case 1: arrive 1 day before at 3,000 m and wake with a headache.** The tool returns high risk; change travel or downgrade the goal to finishing, rather than masking it with painkillers. **Case 2: arrive 10 days early at 4,000 m and run long every day.** Risk is low but overtraining leaves race-day fatigue; reduce volume after arrival. **Case 3: book staging at 3,200 m for a 3,000 m race.** Staging above the race defeats the purpose; choose a lower bed.

## One-line execution

Early arrival is not the goal; a smaller single ascent and protected sleep are. Put the schedule into flights and lodging, put the risk band into the goal; if symptoms appear, descent comes first.

## Related reading

- [Altitude and running](/en/knowledge/altitude-and-running/)
- [Remote trail self-rescue](/en/knowledge/remote-trail-self-rescue/)
- [Race travel planner](/en/tools/race-travel-planner/)

- [Trail and ultra training plan: climbing, time-on-foot, night running, load and back-to-back long sessions](/en/knowledge/trail-ultra-training-plan/)
