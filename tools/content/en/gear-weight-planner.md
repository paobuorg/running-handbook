---
entityId: tool:gear-weight-planner
locale: en
title: "Gear weight planner: weigh every item, total the carried load and flag trade-offs"
summary: "Enter body weight, pack empty weight, water and fuel, plus mandatory and optional gear lists (name, grams, mandatory). The tool totals mandatory and optional weight, base weight, carried load and the share of body weight, identifies the heaviest single item, and flags trade-offs when the load is high or water carry is large. It recommends no brand or replacement purchase; mandatory items follow the current race regulations."
aliases: ["Gear weight planner", "gear weight planner", "trail pack weighing"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

Over a long trail race or a hot road marathon, every extra hundred grams in the pack accumulates across dozens of kilometres, yet the quickest way to cut weight is often to drop safety gear first. This tool records mandatory and optional gear item by item, then adds the pack empty weight, water and fuel to total the base weight and carried load, split mandatory and optional weight, normalise the load against body weight, and identify the heaviest single item. Its purpose is to make weight decisions evidence-based, not to decide what you wear or buy.

It suits runners who sort a trail pack before a race, check mandatory gear, or compare two packing plans, and crew who estimate carried supplies and clothing. It does not suit three situations. First, when you want brand comparison or purchase recommendations; the tool makes no brand judgement. Second, when gear has not been weighed and gram weights are entered from memory; shares and suggestions then drift. Third, when the current edition's mandatory list has not been published and you treat an old regulation's items as today's requirements. The tool estimates a dry packed state; absorbent clothing, layers worn on the body and drop bags are not counted.

## Inputs and units

Body weight is in kilograms; pack empty weight and fuel are in grams; water is in litres. The gear list takes one item per line as `name,grams,mandatory`, where mandatory is 1 for required and 0 for optional; the client groups them into mandatory and optional sets.

| Input | Unit | Required | Range and notes |
| --- | --- | --- | --- |
| `bodyWeightKg` | kg | Yes | Body weight, 30–150 kg |
| `packWeightGrams` | g | Yes | Empty pack weight, 0–5000 g |
| `waterLiters` | L | Yes | Water carried, 0–5 L, converted at 1000 g/L |
| `fuelGrams` | g | Yes | Fuel weight, 0–2000 g |
| `mandatoryItems` | rows | Yes | Gear the rules require, one `name,grams` per line |
| `optionalItems` | rows | Yes | Gear you chose to bring, one `name,grams` per line |

Enter the packed actual weight, not the product nominal weight. Water bottles count with their water; an empty bottle and a full one differ greatly. Small items such as gels and salt tablets count as the whole carried packet. The mandatory flag reflects the rules of the race you enter, not whether you would keep the item. Names stay within 40 characters for readable result tables.

## Formula, assumptions and rounding

The tool validates body weight, pack, water and fuel ranges first, then checks each row's name and grams; the list holds between one and forty items.

- Mandatory weight = sum of mandatory list grams.
- Optional weight = sum of optional list grams.
- Base weight = mandatory weight + pack empty weight.
- Carried load = base weight + optional weight + water × 1000 + fuel.
- Total load = carried load.
- Share of body weight = total load ÷ (body weight × 1000) × 100, one decimal.
- Heaviest item = the single item with the most grams; on a tie, a mandatory item takes priority.
- Trade-off suggestions: a load above 15% of body weight prompts reviewing optional gear first; carrying more than 2 litres prompts checking aid-station spacing and refill opportunities.

Main assumptions: weights are dry and packed; absorbent clothing, body-worn layers and drop bags are excluded; the mandatory flag follows the race rules the entrant holds, and the tool does not re-check the current regulation on race morning; the 15% load and 2-litre water cues are planning heuristics, not official safety limits, and terrain, pace and weather change how a given load feels. Gram totals stay integers; water converts by whole litre; shares keep one decimal.

## How to read the results

The result area shows mandatory weight, optional weight, base weight, carried load, total load, body-weight share and heaviest item first, then the trade-off suggestion list.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Mandatory gear | Weight the rules require | This cannot be cut; only lighter compliant gear reduces it |
| Optional gear | Items you brought without a rule requirement | Cutting decisions start here |
| Base weight | Mandatory gear plus empty pack | See how much the pack itself weighs |
| Carried load | Base plus optional, water and fuel | Compare with past race packing weight |
| Total load | Full carried weight used for the ratio | Check against how the body felt in prior races |
| Share of body weight | Total load as a percentage of body weight | Review optional items first above 15% |
| Heaviest item | The single heaviest piece of gear | Look first for a lighter compliant alternative |
| Suggestions | High-load or large-water-carry cues | Re-weigh and check the mandatory list and aid plan before race day |

Note that high mandatory weight cannot be solved by carrying less, only by choosing lighter compliant gear. The heaviest optional item is not automatically the first to drop; what matters is its race scenario. A low ratio does not prove sensible packing: a simple mandatory list can explain a low total, just as a high total can come from non-negotiable safety gear. The suggestions carry no brand promotion and recommend no specific replacement product.

## Case one: typical

Body weight 62 kg, pack empty 450 g, water 1.5 L, fuel 360 g. Mandatory: waterproof jacket 280 g, headlamp 95 g, survival blanket 120 g, navigation device 180 g. Optional: four gels 240 g, cap 45 g, spare light jacket 320 g.

| Item | Calculation | Result |
| --- | --- | --- |
| Mandatory | 280 + 95 + 120 + 180 | 675 g |
| Optional | 240 + 45 + 320 | 605 g |
| Base weight | 675 + 450 | 1125 g |
| Carried load | 1125 + 605 + 1500 + 360 | 3590 g |
| Share of body weight | 3590 ÷ 62000 × 100 | 5.8% |
| Heaviest item | Spare light jacket 320 g | Review first |

The carried load is 3.59 kg, about 5.8% of body weight, within a normal trail packing range; neither the 15% load cue nor the 2-litre water cue triggers. The spare light jacket is the heaviest single item: with a stable forecast and adequate jacket protection it is the first to review. Gel count, by contrast, should follow race duration and aid-station spacing rather than weight alone. Items such as the headlamp and navigation, though substantial, are never suggested for cutting because they are mandatory.

## Case two: boundary

Body weight 70 kg, pack empty 200 g, water 0 L, fuel 0 g; one mandatory item, survival blanket 200 g, optional list empty.

| Item | Calculation | Result |
| --- | --- | --- |
| Mandatory | 200 | 200 g |
| Optional | 0 | 0 g |
| Base weight | 200 + 200 | 400 g |
| Carried load | 400 + 0 + 0 + 0 | 400 g |
| Share of body weight | 400 ÷ 70000 × 100 | 0.6% |
| Heaviest item | Survival blanket 200 g | No cut candidate |

With one mandatory item, base and carried load both equal mandatory weight plus the pack, and optional is zero; there is nothing to cut, so the suggestion list is empty. This boundary shows the tool does not invent optional items to produce advice, and does not list mandatory gear as candidates. The 0.6% ratio is a mathematical result only and does not mean the packing is complete; real racing still needs fluid, fuel and other gear, which should be listed before judging.

## Case three: invalid or missing input

First, body weight 20 kg falls outside 30–150; the tool rejects it as a range error with field `bodyWeightKg`. Second, pack weight 6000 g falls outside 0–5000; water 6 L falls outside 0–5; fuel 2500 g falls outside 0–2000; an item −50 g or 6000 g falls outside 0–5000; the tool rejects these as range errors. Third, a line missing a comma, with an empty name or non-numeric grams, is rejected at the client as a format error naming the line; these never reach the calculation.

Fourth, an empty browser field for body weight, pack or grams yields a non-finite number, which the tool handles as a non-finite error rather than turning an empty string into zero grams. A mandatory mark written as text other than 1/0 prompts a format issue before the row is grouped.

## Relation to routes and knowledge

Mandatory gear comes from race regulations. The UTMB series publishes a basic mandatory list for all runners and may activate additional items separately according to the forecast; basic and activated items must all be carried at the start. Equipment stays in the pack or belt, accessible and checkable at any time; marshals can inspect packs on course, and refusal to comply can lead to disqualification. Missing safety mandatory gear (water reserve, hooded waterproof jacket, headlamp, survival blanket, smartphone) is disqualifying; other missing mandatory gear carries a time penalty. The regulation also advises against choosing the lightest possible clothing in favour of adequate protection against cold, wind, heavy precipitation and snow. The Western States 100 participant guide requires two LED flashlights each because almost half the trail is run at night; the race is cupless, so runners carry a reusable cup; temperatures range from near freezing to above 110 °F, requiring layered clothing accessible through crew or drop bags; pacers may not carry water, food, lights, shoes or clothing for their runner. Read these alongside the [UTMB](/en/routes/utmb/) route profile.

Fuel weight follows a nutrition position stand: the ISSN ultra-marathon position stand recommends 150–400 kcal per hour during racing, carbohydrate 30–50 g per hour, protein 5–10 g per hour, and fluid 450–750 mL per hour; gut tolerance varies widely, and high intake or hyperosmolar solutions are a primary cause of gastrointestinal distress. Hydration choices are covered in [hydration systems](/en/knowledge/hydration-systems/), fuel and calorie planning in [race fuel comparison](/en/knowledge/race-fuel-comparison/), trail clothing and gear principles in [trail gear](/en/knowledge/trail-gear/), and carry-on checks in the [race checklist](/en/tools/race-checklist/).

## Common failure modes and early signals

The first failure mode is entering gram weights from memory. Product nominal weight excludes water and packaging, and full bottles and spare clothing are often underestimated. Early signal: two packing estimates differ by several hundred grams and you cannot say which item changed.

The second is cutting safety gear first. Under weight pressure, spare insulation, backup light or emergency contact are the easiest things to remove, yet these are often regulation mandatory. Early signal: a flagged mandatory item appears in the suggestions, which means the mandatory mark was set wrong.

The third is reading only total weight, not the mandatory/optional structure. A low total may reflect a simple mandatory list rather than restraint; a high total may come from non-negotiable safety gear. Early signal: at the same 3.5 kg you feel more loaded than others; check the item structure one by one.

The fourth is ignoring absorption and on-course supply. Clothing gains weight with sweat, and bottles are refilled along the way, so pack weight changes through the race; a dry starting total does not represent full-course load. Early signal: bottles were registered empty while you plan self-supported fluid.

## Limits

The tool suits pre-race packing, mandatory-list checking and gear comparison for road marathons and trail running. It does not compare brands, recommend purchases or review products, and it does not assess clothing size, fit or protection level, nor whether gear is adequate for specific weather. It is not medical or safety advice; in mountain weather change, hypothermia or gastrointestinal distress, follow race regulations and the medical process, and gear trade-offs cannot replace safety judgement. Once the current race's mandatory list, weather requirements and aid-station plan are published, the official regulation governs.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, mandatory gear and penalties come from the UTMB 2027 regulations, night lighting, cupless format and temperature range from the Western States 100 participant guide, and fuel and fluid advice from the ISSN ultra-marathon position stand. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Trail gear: clothing, carry and safety equipment principles](/en/knowledge/trail-gear/)
- [Hydration systems: bottles, bladders and carrying methods](/en/knowledge/hydration-systems/)
- [Race fuel comparison: gels, drinks and solid food](/en/knowledge/race-fuel-comparison/)
- [Race checklist: gear and race-day checks](/en/tools/race-checklist/)
- [UTMB route profile and mandatory gear rules](/en/routes/utmb/)

## Sources and scope

The basic and additional mandatory lists, carry-and-inspect requirements, and the disqualification versus time-penalty split for missing safety and other gear come from the UTMB World Series 2027 official regulations. Two LED lights, the cupless format, temperature range, layered clothing and pacer no-muling come from the Western States 100 official participant guide. Per-hour calories, carbohydrate and protein grams, and fluid range come from the ISSN ultra-marathon nutrition position stand. The 15% load cue, 2-litre water cue, heaviest-item rule and gram ranges are planning heuristics of this tool and are not in those official sources. Verified 2026-11-25. Not covered: that edition's specific mandatory gear details and weather-activated items follow the race website regulation.

<!-- related-ring -->
## Related entries

- [Pre-race heat acclimation plan: estimate exposure shortfall and daily schedule from WBGT](/en/tools/heat-acclimation-planner/)
- [Shoe mileage log: track training-shoe distance locally](/en/tools/shoe-mileage/)
- [Sweat-rate estimate — using pre- and post-run body mass and fluid intake](/en/tools/sweat-rate/)
