---
entityId: tool:shoe-mileage
locale: en
title: "Shoe mileage log: track training-shoe distance locally"
summary: "Record each shoe's starting distance, every run and a personal reminder distance. Totals stay in local storage, with no claim of a universal replacement mileage and no upload."
aliases: ["shoe mileage", "shoe tracker", "running shoe log"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool records

Give each shoe a name, enter the distance already on it at purchase (zero if unknown) and the distance at which you want a reminder. After each run, log the date, shoe and distance; the tool totals accumulated distance, run count, distance remaining to the reminder and reminder progress. It is for runners rotating several pairs who want to see actual usage per shoe. It does not recommend brands or models, decide that a shoe is worn out, or diagnose foot or lower-limb pain. The reminder is your own management value, not a manufacturer recommendation or a medical lifespan line.

## Calculation rules and formula

- Total distance = starting distance + the sum of logged run distances for that shoe.
- Remaining distance = max(0, reminder distance − total distance).
- Reminder progress = total distance ÷ reminder distance × 100.
- Run count = number of logged runs for that shoe.
- Last run date = the latest date among that shoe's records.

| Input | Calculation | Output |
| --- | --- | --- |
| Starting 100 km, runs of 10 and 5 km | 100 + 10 + 5 | 115 km |
| Reminder 600 km | max(0, 600 − 115) | 485 km |
| Same | 115 ÷ 600 × 100 | 19.2% |
| Two records | Count | 2 runs, latest date shown |

Everything is calculated locally from your records; no location, track or health data is read.

## Worked example

Assume a daily trainer starts at 100 km with a 600 km reminder and logs 10 km then 5 km: total 115 km, 485 km remaining, progress 115 ÷ 600 × 100 = 19.166…%, shown 19.2%, two runs, latest date 2026-10-28.

A trail shoe starts at 210.5 km with an 800 km reminder and logs 12.4, 8.6 and 15.0 km: total 246.5 km, 553.5 km remaining, progress 30.8125% shown 30.8%, three runs. Independent arithmetic produced both examples.

## Rounding and tolerance

Total and remaining distance keep one decimal with a ±0.05 km tolerance. Reminder progress keeps one decimal with ±0.05 percentage points. Run count is an integer with no tolerance. Single-run distances also keep one decimal, so rounding can accumulate over many entries; check the total against a longer record if precision matters.

## Reading the result

Total distance shows how much a shoe has carried, and progress shows how far it is from your own checkpoint. It does not show remaining life: worn outsole, collapsed foam, a torn upper, asymmetric wear or a new pain matter more than any number. Reaching the reminder is a signal to inspect, not an order to replace. The tool does not automatically allocate runs across a rotation or decide which shoe a session needs.

## How to use it

1. Add each shoe with a name, starting distance and reminder distance; use zero when the starting distance is unknown.
2. Log date, shoe and distance after each run, and check that the total and run count match expectations.
3. Near 100% progress, inspect outsole, foam, upper and how the shoe feels before continuing, demoting it to short runs or replacing it.

## Limits and when not to use it

The reminder is a user preference, not manufacturer or medical advice. Only distances entered in this browser are counted, and records stay local. A log cannot replace inspecting outsole, foam, upper and comfort, and the tool does not track rotation automatically. It is not suitable for recommending brands, declaring a shoe worn out or diagnosing pain, nor for treating mileage as causal evidence of injury. If pain persists, or there is swelling, numbness or a gait change, stop the relevant training and seek qualified medical or sports assessment.

## When this number misleads you

Mileage is only the distance you typed in, and the reminder threshold is your own preference. One missed long run, or logging walks and rides, immediately distorts the remaining kilometres; if rotation is not logged per shoe, two pairs share a single wrong total. Foam, outsole and load tolerance differ so much between models that the same 800 km can be the end of one shoe and early for another.

Do not use it to decide a shoe is finished, to diagnose pain, to recommend a brand, or as causal evidence about injury risk. Outsole wear, foam collapse and comfort need a physical check.

## Related reading

- [Choosing running shoes: fit, cushioning and use](https://learn.paobu.org/en/articles/running-shoes/)
- [Shoe technology: plates, foams and evidence](https://learn.paobu.org/en/articles/shoe-technology/)

## Privacy and data

Records are kept in this browser's localStorage, not uploaded and not tied to an account. Clearing browser data, switching devices or using a private window removes them; export or back them up if they matter. Only shoe names, dates and distances are stored, so avoid addresses, names or other sensitive details in shoe names.

## Sources and scope

Shoe comfort and injury associations follow a secondary analysis; shoe, pain and care guidance follows the NHS; the evidence limits of carbon plates and advanced footwear follow a systematic review. The tool only totals locally and guarantees neither shoe lifespan nor safety. Verified 2026-11-06.
