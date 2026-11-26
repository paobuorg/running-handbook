---
entityId: tool:carb-load-planner
locale: en
title: "Carb-load planner — a usable band from 10–12 g/kg/day over 36–48 hours"
summary: "Enter body mass, race duration and loading window to get a planning band for daily and total carbohydrate, plus a check on whether loading is indicated. The range comes from the 2016 ACSM joint position statement; the tool only does arithmetic and is not a personal dietary prescription."
aliases: ["carb load planner", "carbohydrate loading calculator", "glycogen loading calculator"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool is for

Carb-loading plans fail in two common ways: reading "10–12 g/kg" as "10–12 grams", and concentrating a day's intake into one or two meals. This tool combines body mass, race duration and loading window into a usable band, so you can see roughly how many grams per day and how many grams across the window before deciding how to split the food.

It answers an arithmetic question only: using the 10–12 g/kg/day range from the 2016 ACSM, AND and DC joint position statement, what is your planning band over a 36–48 hour window, and is the race longer than 90 minutes? It does not judge whether you personally need to load, and it does not replace a sports dietitian or doctor.

## Inputs and outputs

There are three inputs: body mass (kg), expected race duration (minutes) and loading window (hours, 36–48). Outputs are whether loading is indicated, the daily carbohydrate lower and upper bounds, the window total lower and upper bounds, and a plain-language note. The daily band answers roughly how many grams to eat per day in the loading period; the window total answers the combined grams across the period; the indication answers whether the race enters the loading scenario under the duration rule. The tool does not calculate food type, fibre, fat, meal frequency or gut tolerance, and it gives no supplement advice.

## Formula and decision rule

```
Daily lower bound = round(body mass × 10)
Daily upper bound = round(body mass × 12)
Window total lower = round(body mass × 10 × window hours / 24)
Window total upper = round(body mass × 12 × window hours / 24)
Indicated = race duration > 90 minutes
```

Input ranges:

| Input | Range | Meaning |
|---|---|---|
| Body mass | 30–200 kg | Converts g/kg into grams |
| Race duration | 1–1440 minutes | Loading is only indicated above 90 minutes |
| Loading window | 36–48 hours | The position statement gives a range, not an exact hour |

"Indicated" uses strictly greater than 90 minutes. Exactly 90 minutes is not indicated, because the statement refers to exercise longer than 90 minutes. This is a conservative boundary rule, not a clinical judgement.

## Worked case 1: 70 kg, 4-hour race, 48-hour window

| Item | Calculation | Result |
|---|---|---|
| Daily lower bound | 70 × 10 | 700 g/day |
| Daily upper bound | 70 × 12 | 840 g/day |
| Window total lower | 700 × 48 / 24 | 1,400 g |
| Window total upper | 840 × 48 / 24 | 1,680 g |
| Indicated | 240 > 90 | Yes |

These values match the published case `case-carb-load-planner-marathon`. A 48-hour window is exactly two days, so the window total is twice the daily band.

## Worked case 2: 60 kg, 45-minute race, 36-hour window

| Item | Calculation | Result |
|---|---|---|
| Daily lower bound | 60 × 10 | 600 g/day |
| Daily upper bound | 60 × 12 | 720 g/day |
| Window total lower | 600 × 36 / 24 | 900 g |
| Window total upper | 720 × 36 / 24 | 1,080 g |
| Indicated | 45 ≤ 90 | No |

These values match the published case `case-carb-load-planner-short-race`. A 45-minute race does not need loading; the tool still calculates a band but clearly flags it as not indicated so the numbers are not mistaken for permission.

## Worked case 3: 65 kg, 2-hour race, 36-hour window (half-day scaling)

| Item | Calculation | Result |
|---|---|---|
| Daily lower bound | 65 × 10 | 650 g/day |
| Daily upper bound | 65 × 12 | 780 g/day |
| Window in days | 36 / 24 | 1.5 days |
| Window total lower | 650 × 1.5 | 975 g |
| Window total upper | 780 × 1.5 | 1,170 g |
| Indicated | 120 > 90 | Yes |

This case checks the non-integer window: 36 hours is 1.5 days, and the window total scales by 1.5 times the daily band rather than rounding to whole days. It matches the published case `case-carb-load-planner-mid-window`.

## Rounding and precision

Daily bounds are first rounded to whole grams with `round(body mass × 10)` and `round(body mass × 12)`; window totals multiply the unrounded daily values by the window hours and then round the final result. Window totals are therefore not "the sum of two rounded daily values" and may differ by 1 g. Input precision limits output precision: if body mass is entered to 0.1 kg, there is no point reading the result to 0.1 g; the tool displays whole grams, and ±1 g is the practical tolerance. This rounding rule affects display only, not the 90-minute applicability test.

## Reading the result

- **Read the indication first.** If loading is not indicated, a normal high-carbohydrate intake in the 24 hours before exercise is the more relevant target, not a 36–48 hour high-dose protocol.
- **Split the daily band across five or six feedings** rather than forcing two or three large meals. If appetite fails, use liquid carbohydrate or easy-to-digest staples, but practise them in training first.
- **Treat the window total as a planning value, not a task to finish.** Eating to the point of discomfort on the last day usually adds gut discomfort rather than glycogen.
- **Do not add training during loading.** High carbohydrate plus high training load tends to carry fatigue into the race.
- **Keep fueling during the race.** Loading raises the starting point; it does not remove the need for hourly carbohydrate.

## Common misconceptions

- **"10–12 grams is enough"** — the unit is 10–12 grams per kilogram of body mass per day; at 70 kg that is 700–840 grams per day.
- **"Longer window is better"** — the statement gives 36–48 hours; extending beyond 48 hours has no additional supporting evidence and only lengthens the high-carbohydrate period.
- **"Every race needs loading"** — there is no clear rationale below 90 minutes, and the tool flags it as not indicated.
- **"Hit the upper bound no matter what"** — the band is a planning range, not a target that must be completed; tolerance and food familiarity matter more.
- **"Loading means no race fuel"** — glycogen and fluid are still used during the race, and long events still need hourly carbohydrate.

## Assumptions and exclusions

- The band is for sustained or intermittent exercise longer than 90 minutes, not for 5K, 10K or most half marathons;
- The tool does not calculate food type, fibre, fat, meal frequency or gut tolerance;
- It does not handle diabetes, eating disorders, pregnancy, postpartum status, gastrointestinal disease or other conditions needing medical nutrition management;
- It gives no supplement, iron, vitamin or electrolyte advice;
- It does not determine whether you already have low energy availability or malnutrition;
- The result is a planning band, not a prescription, and it does not guarantee performance.

People with diabetes, insulin resistance, a history of eating disorders, irritable bowel syndrome, chronic diarrhoea, gastro-oesophageal reflux, or who are pregnant, postpartum, adolescent or actively losing weight should adjust with a doctor or registered dietitian rather than applying the tool's numbers directly.

## Boundaries

This tool is a nutrition planning aid. It does not diagnose, give medication advice or constitute a personal dietary prescription. The range comes from the ACSM, AND and DC joint position statement; execution should be individualised by a registered sports dietitian using your body mass, race, medical history and tolerance. Persistent vomiting, severe abdominal pain, inability to eat, fainting or chest pain should be treated as an emergency. The site provides no medical diagnosis, weight-loss or weight-gain advice.

## When this number misleads you

The band only has a job when the event lasts longer than 90 minutes; 5K, 10K and most half marathons do not need glycogen loading, so the number has no scenario to apply to. Even then, entering body mass 5 kg too high shifts the daily total by roughly 50–60 g at 10–12 g/kg/day, and the 36–48 hour window is a planning band, not a switch that must flip at a particular hour. The tool also assumes your gut tolerates a high-carbohydrate diet; bloating, diarrhoea or loss of appetite make the paper number fail in a way it cannot see.

Do not use it to diagnose low energy availability or to judge nutritional adequacy, and do not substitute it for dietetic care in diabetes, eating disorders, pregnancy or gastrointestinal disease. "Eating the number" is not modelled as a performance guarantee, and this is not medical or dietetic advice.

## How to use it

1. Check whether the expected race duration exceeds 90 minutes; below 90 minutes, treat the output as reference only and do not run a loading protocol.
2. Enter body mass and planned window, read the daily band and window total, then split them into meals using foods already tested in training.
3. Practise race-day carbohydrate foods and drinks in the week before, record gut reactions, and consult a professional if you have underlying conditions or dietary restrictions.

## Related reading

- [Carbohydrate loading: dose, timing and gut cost](/en/knowledge/carb-loading/)
- [Race-day fuelling: how much per hour](/en/knowledge/race-day-fueling/)
- [Long-run fuelling: before, during and after](/en/knowledge/long-run-fueling/)
- [Gut training: what you can take on race day](/en/knowledge/gut-training-for-races/)

## Sources and scope

- ACSM, AND and DC, Nutrition and Athletic Performance (joint position statement, 2016): events longer than 90 minutes, 10–12 g/kg per day for the 36–48 hours before exercise; 30–60 g/h for 1–2.5 hours and up to 90 g/h beyond 2.5 hours; individualised advice.
- Beck et al., Role of nutrition in performance enhancement and postexercise recovery (review, 2015): loading for events longer than 90 minutes; no clear advantage for 60–90 minutes; 7–12 g/kg in the 24 hours before shorter events; depletion phase unnecessary.
- ISSN carbohydrate-timing review: pre-, during and post-exercise carbohydrate rhythm and per-hour dose guidance, used to explain that race fuelling still applies; it does not enter the loading band calculation.

The tool and this page were verified on 2026-11-26.

<!-- related-ring -->
## Related entries

- [Race fuelling plan: estimate carbohydrate by the hour](/en/tools/fueling-planner/)
- [Gear weight planner: weigh every item, total the carried load and flag trade-offs](/en/tools/gear-weight-planner/)
- [Pre-race heat acclimation plan: estimate exposure shortfall and daily schedule from WBGT](/en/tools/heat-acclimation-planner/)
