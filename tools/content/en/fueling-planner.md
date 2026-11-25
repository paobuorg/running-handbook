---
entityId: tool:fueling-planner
locale: en
title: "Race fuelling plan: estimate carbohydrate by the hour"
summary: "From planned duration and carbohydrate per serving, return a 30–60 g/h planning range, totals and servings. It does not calculate fluid and does not replace testing in training."
aliases: ["fuelling planner", "carbohydrate plan", "race fuel"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates

Enter a planned exercise duration and the carbohydrate grams in one serving of gel, drink or food. The tool uses a 30–60 g/h planning range to estimate total carbohydrate, servings and a rough distribution rhythm. It is for runners preparing fuel for a long session and for coaches checking a carry plan. Sessions under 60 minutes do not add carbohydrate. It is not an individual prescription and does not calculate fluid or sodium. If you have diabetes, a gastrointestinal condition, are pregnant, have a history of eating disorders or take medication, consult a clinician or dietitian rather than adopting the output directly.

## Calculation rules and formula

For sessions of at least 60 minutes, plan 30 to 60 grams of carbohydrate per hour:

- Duration hours = planned minutes ÷ 60.
- Low total = 30 × duration hours.
- High total = 60 × duration hours.
- Low servings = ⌈low total ÷ carbohydrate per serving⌉.
- High servings = ⌈high total ÷ carbohydrate per serving⌉.
- Under 60 minutes: totals and servings are both zero.

| Input | Calculation | Output | Use |
| --- | --- | --- | --- |
| 90 minutes, 25 g per serving | 1.5 hours × 30/60 | 45–90 g | Planned total |
| Same | 45÷25 and 90÷25, rounded up | 2–4 servings | Carry count |
| 45 minutes | Under 60 minutes | 0 g, 0 servings | No added carbohydrate |
| 180 minutes, 30 g per serving | 3 hours × 30/60 | 90–180 g | Long-session total |

Servings round up so you carry enough; actual intake still needs adjustment in training.

## Worked example

- 90 minutes at 25 g per serving: 1.5 hours, low 30 × 1.5 = 45 g, high 60 × 1.5 = 90 g; servings 45 ÷ 25 = 1.8 → 2 and 90 ÷ 25 = 3.6 → 4.
- 45 minutes at 25 g per serving: under 60 minutes, so 0 g and 0 servings.
- 180 minutes at 30 g per serving: 3 hours, 90 g and 180 g, with 3 and 6 servings.

These values follow independent arithmetic and can be repeated from a product label.

## Rounding and tolerance

Total carbohydrate is reported in whole grams with a ±0.5-gram tolerance. Servings round up to a whole serving, so the count can only be higher than the exact value, never lower. Duration is reported in hours to two decimals with a ±0.005-hour (about ±18-second) tolerance. Rounding up can exceed the high total: four servings at 25 g is 100 g, above the 90 g planning upper bound. That is a carry margin, not an instruction to eat everything.

## Reading the result

The totals and servings describe what to prepare, not what must be consumed. Actual intake depends on intensity, weather, gastrointestinal tolerance and training habits. Heat or high intensity may raise demand, while poor tolerance calls for lower concentration or smaller servings. The upper serving count is a carry reference, not a race-day prescription. Fluid, sodium, calories and blood-glucose response are not estimated.

## How to use it

1. Enter the planned duration (10 to 1,440 minutes) and carbohydrate grams per serving from the label (5 to 100 g).
2. Read the low and high totals and servings, then distribute them across the aid stations.
3. Trial the same products at a similar intensity and duration in training, note gastrointestinal response, and adjust race-day amounts.

## Limits and when not to use it

The 30–60 g/h range is planning guidance, not an individual prescription. Carbohydrate per serving must come from the label, because gels and drinks vary. Fluid and sodium are excluded because sweat rate and conditions vary widely. The plan must be tested in training and adjusted for tolerance, duration and intensity. The tool is not suitable for disease-specific diets or cases needing a dietitian.

## When this number misleads you

The 30–60 g/h range assumes each serving's carbohydrate is read accurately from the label. A 22 g gel and a 40 g gel are nearly a factor of two apart at the same "two servings per hour", and the tool will not check the packets for you. Beyond about three hours, the top of the 30–60 g/h band may be too low for some runners; going higher depends on multiple-transportable carbohydrate products and a gut already tested in training. The site's knowledge article only gives the general 30–60 g/h range, and the tool does not decide your individual ceiling. Conversely, if gastric emptying cannot keep up, the carbohydrate on the plan does not become available energy.

Do not use it as an individual fluid or sodium prescription, or to diagnose gastrointestinal disease, hypoglycaemia or dehydration. It is a starting draft that must be tested in training before race day, and it is not medical or dietetic advice.

## Related reading

- [Long-run fuelling: from practice to race day](https://learn.paobu.org/en/articles/long-run-fueling/)
- [Hydration: how much and when](https://learn.paobu.org/en/articles/hydration/)
- [Race-day fuelling: take what you have already tested](https://learn.paobu.org/en/articles/race-day-fueling/)

## Privacy and data

All calculations happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. Clear the address-bar parameters after using a shared device.

## Sources and scope

The carbohydrate range follows the ISSN carbohydrate and nutrient-timing position stands; hydration guidance follows the NHS; the relationship between duration and intensity can be read with the CDC intensity description. The tool uses a conservative 30–60 g/h range and does not replace sports-nutrition or medical assessment. Verified 2026-11-06.
