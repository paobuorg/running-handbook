---
entityId: tool:sweat-rate
locale: en
title: "Sweat-rate estimate — using pre- and post-run body mass and fluid intake"
summary: "Enter body mass before and after exercise, fluid swallowed during the session and duration to estimate net fluid loss, sweat rate per hour and body mass loss percentage using the ACSM weighing method, with a 2% flag. It is arithmetic on one measurement, not a fixed sweat rate or a hydration prescription."
aliases: ["sweat rate", "sweat rate calculator", "fluid loss calculator", "hydration estimate"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool is for

"How much should I drink?" needs a measurable starting point: **how much fluid did this session actually cost**. The 2007 ACSM position stand on exercise and fluid replacement gives the method — weigh before and after exercise, and add back the fluid consumed during the session. This tool turns that method into repeatable arithmetic so you can build a personal reference across different weather and intensities.

It does not predict your next sweat rate, and it does not tell you to hit a fixed number. A single result is affected by weather, intensity, clothing, heat acclimatisation, menstrual cycle and illness; judging a typical sweat rate needs repeated measurements under similar conditions. The output is an estimate for this one session, not a fixed long-term sweat standard.

## Inputs and outputs

There are four inputs: body mass before exercise (kg), body mass after exercise (kg), fluid actually swallowed during the session (L), and exercise duration (minutes). Outputs are net fluid loss (L), estimated sweat rate (L/h), body mass loss percentage, and a flag for whether the loss exceeds 2% of body mass, plus a plain-language note. Net loss answers how much water was lost once the scale change and fluid drunk are combined; sweat rate answers the per-hour equivalent; the body-mass percentage is what the 2% flag uses. The tool does not calculate sodium loss and does not output a drinking prescription.

## Usage steps

1. Empty your bladder before the run, wear similar clothing, and weigh yourself on the same scale; record the value.
2. Record only the fluid you actually swallow during the run; pours, mouthfuls spat out and liquid left in the bottle do not count.
3. Dry yourself, remove wet clothing and weigh again on the same scale.
4. Enter both weights, the volume drunk and the duration; check whether net loss is negative, then read sweat rate and the 2% flag, and use "Reading the result" to decide what this single measurement can and cannot say.

## Formula

```
Net loss (L) = pre-exercise body mass − post-exercise body mass + fluid intake
Sweat rate (L/h) = net loss ÷ (duration / 60)
Body mass loss (%) = (pre-exercise body mass − post-exercise body mass) ÷ pre-exercise body mass × 100
Above 2% = body mass loss (rounded to 2 decimals) > 2
```

Input ranges:

| Input | Range | Notes |
|---|---|---|
| Body mass before exercise | 30–200 kg | Empty bladder, similar clothing, same scale |
| Body mass after exercise | 30–200 kg | Towel dry and remove wet clothing before weighing |
| Fluid consumed during exercise | 0–10 L | Count only what was actually swallowed |
| Exercise duration | 1–1440 minutes | Used to convert net loss to an hourly rate |

If the combination implies a negative net loss (for example, finishing heavier than starting while also logging a large intake), the tool reports an error and asks you to check the weighings and intake rather than returning a negative sweat rate.

## Worked example 1: a 60-minute regular session

**Example 1: 70 kg, 60 minutes, 69.2 kg afterwards, 0.5 L consumed**

- Net loss = 70 − 69.2 + 0.5 = **1.3 L**
- Sweat rate = 1.3 ÷ 1 = **1.3 L/h**
- Body mass loss = (70 − 69.2) ÷ 70 × 100 = **1.14%**
- 2% flag: **not exceeded**

This sweat rate is not low, but the body-mass loss stays inside the threshold; a high hourly sweat rate is not the same as excessive dehydration.

## Worked example 2: a 90-minute longer session

**Example 2: 60 kg, 90 minutes, 59.1 kg afterwards, 0.3 L consumed**

- Net loss = 60 − 59.1 + 0.3 = **1.2 L**
- Sweat rate = 1.2 ÷ 1.5 = **0.8 L/h**
- Body mass loss = (60 − 59.1) ÷ 60 × 100 = **1.5%**
- 2% flag: **not exceeded**

Ninety minutes is scaled to 1.5 hours, so the sweat rate is lower than in example one. The threshold applies to the body-mass percentage, not to litres per hour.

## Worked example 3: above the 2% body-mass loss

**Example 3: 65 kg, 60 minutes, 63.5 kg afterwards, 0.4 L consumed**

- Net loss = 65 − 63.5 + 0.4 = **1.9 L**
- Sweat rate = 1.9 ÷ 1 = **1.9 L/h**
- Body mass loss = (65 − 63.5) ÷ 65 × 100 = **2.31%**
- 2% flag: **exceeded**

This case checks the percentage threshold: at roughly 1.9 L/h, a 65 kg runner loses 2.31% of body mass, above the 2% flag. The flag is a review prompt, not a diagnosis. Weakness, dizziness, nausea or headache suggest stopping the session; confusion, slurred speech, very high temperature or loss of consciousness is an emergency — call first and cool while waiting.

## How to use the 2% flag

ACSM sets the goal of drinking during exercise as **preventing more than 2% body mass loss** and avoiding large changes in electrolyte balance. The tool turns that into a prompt, not a diagnosis:

- Above 2%: this session is worth reviewing — weather, intensity, intake or duration. Adjust the fluid plan for similar conditions next time.
- At or below 2%: this session stayed within the threshold; still repeat the measurement in different conditions before treating it as your typical value.

The denominator is pre-exercise body mass, so the same 1.4 L loss is about 2.0% for a 70 kg runner and about 2.3% for a 60 kg runner. That is why the tool asks for body mass instead of reporting only litres per hour.

### Case matrix

Existing cases side by side by input, expected output and coverage. Values come from `data/cases`; nothing is re-derived by hand.

| Case | Input | Expected | Coverage |
|---|---|---|---|
| `case-sweat-rate-hour-run` | `{"preWeightKg":70,"postWeightKg":69.2,"fluidIntakeLiters":0.5,"durationMinutes"…` | `{"netLossLiters":1.3,"sweatRateLitersPerHour":1.3,"bodyMassLossPercent":1.14,"a…` | Typical |
| `case-sweat-rate-ninety-minutes` | `{"preWeightKg":60,"postWeightKg":59.1,"fluidIntakeLiters":0.3,"durationMinutes"…` | `{"netLossLiters":1.2,"sweatRateLitersPerHour":0.8,"bodyMassLossPercent":1.5,"ab…` | Second unit/boundary |
| `case-sweat-rate-over-two-percent` | `{"preWeightKg":65,"postWeightKg":63.5,"fluidIntakeLiters":0.4,"durationMinutes"…` | `{"netLossLiters":1.9,"sweatRateLitersPerHour":1.9,"bodyMassLossPercent":2.31,"a…` | Third unit |

## Reading the result

- **Net loss** is the fluid deficit for this session, not a "level of dehydration"; it combines the scale change with the volume drunk.
- **Sweat rate (L/h)** is comparable only across similar weather, intensity, clothing and duration; one cool morning run cannot be scaled to a hot race.
- **Body-mass loss percentage** is the input to the 2% flag; losing the same 1.3 L produces different percentages at 70 kg and 60 kg.
- **The 2% flag** is a screening prompt, not a diagnosis, and crossing 2% does not guarantee a problem; it tells you to review the fuelling plan.
- This number **says nothing about sodium loss** and cannot prescribe sodium intake; salt and electrolyte plans need separate evidence.

## Common misconceptions

| Misconception | More accurate statement |
|---|---|
| "More sweat means a better session" | Sweat rate mainly reflects environment, intensity and individual variation, not training quality |
| "Everyone should drink 1 L/h" | Individual variation is large; ACSM explicitly recommends customised programmes, starting with your own weighing measurement |
| "Weight lost in a session is fat loss" | The acute change is mostly water and cannot be used to estimate fat change |
| "You should finish at exactly the same weight" | Losing less than 2% of body mass during exercise is common and acceptable; zero loss is not the target |

## Assumptions and limits

- The calculation assumes body mass change reflects mainly sweat loss and consumed fluid; urine, stool, substrate oxidation and metabolic water are not measured separately.
- It needs the same scale, similar clothing and a consistent weighing routine; household scale precision feeds straight into the result.
- Fluid intake must be the volume actually swallowed, excluding spills, fluid held in the mouth or left in the bottle.
- Sweat sodium loss is outside the calculation; whether water alone is appropriate after heavy sweating depends on duration, intensity and the individual.
- The tool does not diagnose dehydration, heat illness, kidney or cardiac problems, and gives no hydration or medication prescription. People with relevant medical conditions, on medication or pregnant should ask a clinician first.

## Boundaries

This tool is a post-session weighing estimate, not a medical diagnosis, and it does not constitute a fluid or weight-loss prescription. The 2% threshold comes from the ACSM position stand's anti-dehydration goal and is a screening marker; a personal fluid plan should account for duration, environment, sweat composition and prior health. With persistent dizziness, fainting, altered consciousness, chest pain or inability to keep fluids down, stop exercise and seek medical help.

## When this number misleads you

It assumes the change in body mass is mainly sweat plus the fluid you drank; urine, stool, metabolic water and substrate oxidation are not measured. A household scale error of 0.1 kg over a 60-minute session is a 0.1 L/h error in sweat rate, the same order as a real difference between sessions. One measurement represents only that weather, intensity, clothing and acclimatisation state and cannot be scaled to a hotter or longer run. The 2% flag is a screening marker.

Do not use it as a drinking prescription or a sodium requirement, or to diagnose dehydration or heat illness; during pregnancy, on medication, or with kidney or heart conditions, do not change fluid intake based on this number. It is not medical advice.

## Related reading

- [Hydration: how much and when](/en/knowledge/hydration/)
- [Heat and humidity: risk, acclimatisation and adjustment](/en/knowledge/heat-and-humidity/)
- [Electrolytes and sodium: sweat loss and replacement](/en/knowledge/electrolytes-and-sodium/)
- [Race-day fuelling: carbohydrate, fluid and rhythm](/en/knowledge/race-day-fueling/)

## Sources and scope

- American College of Sports Medicine, Exercise and Fluid Replacement position stand (2007): the goal of drinking during exercise is to prevent more than 2% body mass loss and excessive electrolyte changes; individual sweat rate can be estimated from body mass before and after exercise; sweating rate and sweat electrolyte content vary considerably between individuals, so customised programmes are recommended.
- NHS, Water, drinks and hydration: daily hydration can be checked against urine colour, and longer or hotter activity may require more fluid; this is general hydration advice, not a substitute for measuring your own sweat rate.
- U.S. National Weather Service heat-illness page: heat-exhaustion and heat-stroke signs and the call-first, cool-while-waiting instruction, used to set stop-signal boundaries; it does not enter the sweat-rate calculation.

This page was verified on 2026-11-26.

<!-- related-ring -->
## Related entries

- [Running pain self-check: seven questions before deciding on assessment](/en/tools/injury-risk-check/)
- [Course comparison: compare published versions field by field](/en/tools/route-compare/)
- [Route elevation: a local GPX elevation profile](/en/tools/route-elevation/)
