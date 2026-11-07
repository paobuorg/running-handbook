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

It does not predict your next sweat rate, and it does not tell you to hit a fixed number. A single result is affected by weather, intensity, clothing, heat acclimatisation, menstrual cycle and illness; judging a typical sweat rate needs repeated measurements under similar conditions.

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

## Worked examples

**Example 1: 70 kg, 60 minutes, 69.2 kg afterwards, 0.5 L consumed**

- Net loss = 70 − 69.2 + 0.5 = **1.3 L**
- Sweat rate = 1.3 ÷ 1 = **1.3 L/h**
- Body mass loss = (70 − 69.2) ÷ 70 × 100 = **1.14%**
- 2% flag: **not exceeded**

**Example 2: 60 kg, 90 minutes, 59.1 kg afterwards, 0.3 L consumed**

- Net loss = 60 − 59.1 + 0.3 = **1.2 L**
- Sweat rate = 1.2 ÷ 1.5 = **0.8 L/h**
- Body mass loss = (60 − 59.1) ÷ 60 × 100 = **1.5%**
- 2% flag: **not exceeded**

Both examples sit below 2%, which shows that a high hourly sweat rate is not the same as excessive dehydration. The threshold applies to body mass loss percentage, not to litres per hour.

## How to use the 2% flag

ACSM sets the goal of drinking during exercise as **preventing more than 2% body mass loss** and avoiding large changes in electrolyte balance. The tool turns that into a prompt, not a diagnosis:

- Above 2%: this session is worth reviewing — weather, intensity, intake or duration. Adjust the fluid plan for similar conditions next time.
- At or below 2%: this session stayed within the threshold; still repeat the measurement in different conditions before treating it as your typical value.

The denominator is pre-exercise body mass, so the same 1.4 L loss is about 2.0% for a 70 kg runner and about 2.3% for a 60 kg runner. That is why the tool asks for body mass instead of reporting only litres per hour.

## Assumptions and limits

- The calculation assumes body mass change reflects mainly sweat loss and consumed fluid; urine, stool, substrate oxidation and metabolic water are not measured separately.
- It needs the same scale, similar clothing and a consistent weighing routine; household scale precision feeds straight into the result.
- Fluid intake must be the volume actually swallowed, excluding spills, fluid held in the mouth or left in the bottle.
- Sweat sodium loss is outside the calculation; whether water alone is appropriate after heavy sweating depends on duration, intensity and the individual.
- The tool does not diagnose dehydration, heat illness, kidney or cardiac problems, and gives no hydration or medication prescription. People with relevant medical conditions, on medication or pregnant should ask a clinician first.

## When this number misleads you

It assumes the change in body mass is mainly sweat plus the fluid you drank; urine, stool, metabolic water and substrate oxidation are not measured. A household scale error of 0.1 kg over a 60-minute session is a 0.1 L/h error in sweat rate, the same order as a real difference between sessions. One measurement represents only that weather, intensity, clothing and acclimatisation state and cannot be scaled to a hotter or longer run. The 2% flag is a screening marker.

Do not use it as a drinking prescription or a sodium requirement, or to diagnose dehydration or heat illness; during pregnancy, on medication, or with kidney or heart conditions, do not change fluid intake based on this number. It is not medical advice.

## Related reading

- [Hydration: how much and when](https://learn.paobu.org/en/articles/hydration/)
- [Heat and humidity: risk, acclimatisation and adjustment](https://learn.paobu.org/en/articles/heat-and-humidity/)

## Common misconceptions

| Misconception | More accurate statement |
|---|---|
| "More sweat means a better session" | Sweat rate mainly reflects environment, intensity and individual variation, not training quality |
| "Everyone should drink 1 L/h" | Individual variation is large; ACSM explicitly recommends customised programmes, starting with your own weighing measurement |
| "Weight lost in a session is fat loss" | The acute change is mostly water and cannot be used to estimate fat change |
| "You should finish at exactly the same weight" | Losing less than 2% of body mass during exercise is common and acceptable; zero loss is not the target |

## Sources

- American College of Sports Medicine, Exercise and Fluid Replacement position stand (2007): the goal of drinking during exercise is to prevent more than 2% body mass loss and excessive electrolyte changes; individual sweat rate can be estimated from body mass before and after exercise; sweating rate and sweat electrolyte content vary considerably between individuals, so customised programmes are recommended.

This page was verified on 2026-11-07.
