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

## Inputs and outputs

Inputs come in two groups: the shoe itself (name, starting distance, reminder distance) and each run record (date, distance). Outputs are total mileage, remaining distance to the reminder, reminder progress and run count, plus the latest logged date. Total mileage shows how much the shoe has carried; progress shows how far it is from your own checkpoint; the run count helps spot missed entries or duplicates. The tool does not read location, track, heart rate or body mass, and it does not automatically fold walks, hikes or rides into the running-shoe mileage.

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

Everything is calculated locally from your records. The reminder distance in the formula is set by the user; the tool never infers a universal replacement mileage. Foam and outsole wear vary with shoe model, body mass, surface and running form, so one mileage threshold cannot apply to every pair.

## Worked example 1: a typical daily trainer

Assume a daily trainer starts at 100 km with a 600 km reminder and logs 10 km then 5 km: total 115 km, 485 km remaining, progress 115 ÷ 600 × 100 = 19.166…%, shown 19.2%, two runs, latest date 2026-10-28. This example matches ordinary check-in progress under a steady volume. The figures follow independent arithmetic, not the page script's own output.

## Worked example 2: decimal accumulation on a trail shoe

A trail shoe starts at 210.5 km with an 800 km reminder and logs 12.4, 8.6 and 15.0 km: total 246.5 km, 553.5 km remaining, progress 30.8125% shown 30.8%, three runs. Decimal distances are summed item by item and kept to one decimal. Trail surfaces, stones, mud and downhill impact wear the outsole faster, but the mileage number itself does not distinguish surface type. This case checks decimal addition and rounding of the progress percentage.

## Worked example 3: past the reminder (common pitfall)

Assume a shoe starts at 580 km with a 600 km reminder and logs two 15 km runs: total 580 + 15 + 15 = 610 km. Remaining distance uses max(0, 600 − 610) = 0 km; the tool never reports a negative remaining value. Progress is 610 ÷ 600 × 100 = 101.666…%, shown 101.7%, and may exceed 100%; two runs, latest date 2026-11-25. The common mistakes are reporting a remaining mileage of −10 km, or capping progress at 100%. Crossing the reminder is an inspection signal, not an automatic replacement verdict.

## Rounding and tolerance

Total and remaining distance keep one decimal with a ±0.05 km tolerance. Reminder progress keeps one decimal with ±0.05 percentage points. Run count is an integer with no tolerance. Single-run distances also keep one decimal, so rounding can accumulate over many entries; check the total against a longer record if precision matters. When recomputing by hand, keep unrounded intermediate values rather than dividing figures that have already been rounded to one decimal.

## Reading the result

Total distance shows how much a shoe has carried, and progress shows how far it is from your own checkpoint. It does not show remaining life: worn outsole, collapsed foam, a torn upper, asymmetric wear or a new pain matter more than any number. Reaching the reminder is a signal to inspect, not an order to replace. The tool does not automatically allocate runs across a rotation or decide which shoe a session needs. Rotation records must be logged per shoe to show the true usage of each pair.

## Common pitfalls

The first pitfall is treating mileage as a lifespan line: at the same 600 km, wear differs widely with body mass, surface and form, so mileage is an inspection reminder rather than a wear-out standard. The second is counting walks, hikes and rides toward running-shoe mileage, which distorts the total. The third is logging several pairs under one name, so rotation ends up sharing a single wrong total. The fourth is trusting the number over the physical shoe: foam feel, outsole pattern, upper structure and landing comfort need a hands-on check that a figure cannot replace.

## Limits and when not to use it

The reminder is a user preference, not manufacturer or medical advice. Only distances entered in this browser are counted, and records stay local. A log cannot replace inspecting outsole, foam, upper and comfort, and the tool does not track rotation automatically. It is not suitable for recommending brands, declaring a shoe worn out or diagnosing pain, nor for treating mileage as causal evidence of injury. If pain persists, or there is swelling, numbness or a gait change, stop the relevant training and seek qualified medical or sports assessment. The tool gives no weight-loss, weight-training or foot-disorder treatment advice.

## How to use it

1. Add each shoe with a name, starting distance and reminder distance; use zero when the starting distance is unknown.
2. Log date, shoe and distance after each run, and check that the total and run count match expectations.
3. Near 100% progress, inspect outsole, foam, upper and how the shoe feels before continuing, demoting it to short runs or replacing it.

## Related reading

- [Choosing running shoes: fit, cushioning and use](/en/knowledge/running-shoes/)
- [Shoe technology: plates, foams and evidence](/en/knowledge/shoe-technology/)
- [Last, fit and cushioning](/en/knowledge/shoe-fit-and-cushioning/)
- [Achilles tendon pain in runners](/en/knowledge/achilles-tendon-pain/)

## Privacy and data

Records are kept in this browser's localStorage, not uploaded and not tied to an account. Clearing browser data, switching devices or using a private window removes them; export or back them up if they matter. Only shoe names, dates and distances are stored, so avoid addresses, names or other sensitive details in shoe names.

## Sources and scope

Shoe comfort and injury associations follow a secondary analysis; shoe, pain and care guidance follows the NHS; the evidence limits of carbon plates and advanced footwear follow a systematic review. The tool only totals locally and guarantees neither shoe lifespan nor safety. Where a parameter lacks a traceable basis, the text labels it as an estimate rather than inventing a precise constant. Verified 2026-11-26.

<!-- related-ring -->
## Related entries

- [Sweat-rate estimate — using pre- and post-run body mass and fluid intake](/en/tools/sweat-rate/)
- [Running pain self-check: seven questions before deciding on assessment](/en/tools/injury-risk-check/)
- [Course comparison: compare published versions field by field](/en/tools/route-compare/)
