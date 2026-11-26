---
entityId: knowledge:training-pace-zones
locale: en
title: "Training pace zones: official guidance, coaching systems and what can be verified"
summary: "After checking ACSM, England Athletics, Daniels' VDOT and McMillan, one conclusion holds: no official body publishes percentage-based training pace zones derived from race results. The tables come from coaching systems and commercial tools. This page explains their assumptions, where they disagree and how large the error is, and which parts can be verified."
aliases:
  - training pace zones
  - pace zones
  - VDOT
  - training paces
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## Definition and scope

"Training pace zones" divide training into intensity bands and give each band a pace range — easy, marathon, threshold, interval. A common method converts a recent race result into "current fitness" and then derives paces for each zone.

This page asks a more basic question: **who actually set those percentages and zones?** It is for runners using a pace table or wondering whether to trust a calculator. It does not provide a personal training plan, and it does not treat any commercial system as an official standard.

## The finding: only coaching systems provide this

Checking whether any official or authoritative body publishes percentage-based pace zones derived from race performance gives three results:

- **No official body publishes such a percentage pace table.** ACSM anchors intensity to percentage of maximal heart rate, heart-rate reserve, RPE, the talk test and step rate; England Athletics uses heart-rate percentages and RPE, with intervals described as "3K–10K race pace".
- **Pace ranges come from coaching systems and commercial tools.** Jack Daniels' VDOT system converts race results into a fitness value and then into training paces; the McMillan Running Calculator divides training into four zones with pace ranges, alongside heart rate and RPE. Neither is a document from a government, medical society or athletics federation.
- **The classification for this page is therefore the second option: these systems rest on explainable assumptions, disagree with each other and cannot be treated as official standards.** The assumptions, differences and error evidence are set out below.

## What official bodies do and do not provide

| Body and document | Intensity anchors | Percentage pace zones from race results? |
|---|---|---|
| ACSM, Tips for Monitoring Aerobic Exercise Intensity | Moderate **65%–75% HRmax**, vigorous **76%–96% HRmax**; RPE 3–4 and 5–7; talk test; step rate | **No.** Anchors are heart rate, perceived effort and step rate, not race-derived paces |
| England Athletics, Training pace (2024) | Easy **60%–75% HRmax**, RPE 2–3; steady RPE 4–5; threshold RPE 7–8; intervals about **3K–10K race pace** | **No.** The article notes that threshold measurement is not available to everyone and pace is guided more by feel |
| Clinical guidance (NICE, NHS) | Not about training pace | Not applicable |

The comparison shows that official guidance can answer "how hard should this run feel", but not "what should my threshold pace be in minutes per kilometre". The latter needs a model mapping race results to physiology and physiology to pace — and that model currently comes from coaching systems.

## How the coaching systems calculate paces

**Daniels VDOT** estimates a fitness value (VDOT, essentially a VO₂max estimate adjusted for running economy) from a recent race, then assigns training paces for easy (E), marathon (M), threshold (T), interval (I) and repetition (R) work. It chains "result — fitness — pace", and every link depends on assumptions.

**McMillan Running Calculator** also starts from a recent race, produces "equivalent" times at other distances, then divides training into Endurance, Stamina, Speed and Sprint zones with pace ranges for specific workouts, alongside %HRmax, %heart-rate reserve and RPE. Its own guide calls these **estimates** and recommends recalculating every 4–8 weeks as fitness changes.

Both are useful, but their zone names, boundaries and workout categories differ: one uses E/M/T/I/R, the other four workout zones. Mixing the two tables can produce two different "correct" paces for the same session.

## Assumptions shared by these systems

1. **A recent race represents current fitness.** This assumes a maximal effort, flat course, normal weather and no illness or training interruption.
2. **Performances at different distances are equivalent.** This relies on a power-law or fitted model; the further apart the distances, the larger the error. McMillan's guide itself says a 5 km result should not be used to predict a marathon unless the runner has trained for the marathon.
3. **Physiological markers map reliably onto pace.** "Threshold pace" assumes the intensity at lactate threshold can be described by the same percentage across individuals, but threshold moves with training, fatigue, terrain and temperature.
4. **The runner is trained, uninjured and economically stable.** Beginners, runners returning from injury, trail runners and hot conditions do not meet these assumptions.

If any assumption fails, the seconds in the table are a starting point rather than "your pace".

## Disagreement and error: the hard evidence

- **VDOT underestimates VO₂max.** Scudamore et al. (2018) tested VDOT against laboratory data in 11 NCAA Division 1 athletes and 9 recreational runners using indoor 5 km time trials. VDOT significantly underestimated VO₂max in both groups (d = 1.75 and 3.44), with a larger gap in recreational runners (d = 1.59); reported average error was about **4.7%** in athletes and **9.2%** in recreational runners.
- **Different products of the same system disagree.** Blödorn and Döring (2025) noted that VDOT tables and the VDOT online calculator differ above 1500 m, by about **10 seconds** over 5000 m; Riegel's original exponent is **1.07732**, while the online calculator uses **1.06**. "Equivalent performance" is not a single answer.
- **Zone paces are not equally appropriate at every level.** In the same 2018 study, VDOT's recommended interval pace was slower than measured VO₂max pace in recreational runners (d = 1.76) but not different in athletes; recommended threshold pace was faster than measured lactate-threshold pace in athletes (d = 1.49) but not different in recreational runners. The authors concluded that threshold pace can be used with confidence, while interval pace may not be optimal for raising VO₂max in recreational runners.
- **The commercial tool calls itself an estimate.** McMillan's guide labels equivalent performances as estimates, stresses that course, weather and day-to-day condition change the outcome, and recommends recalculation every 4–8 weeks.

Taken together, the conclusion is not "tables are useless" but: **a table is a starting point with error, not a standard answer; different tables cannot be calibrated into an official consensus.**

## What can be verified, and how to use it

| Question | Verifiable anchor | Error and limits |
|---|---|---|
| How hard should this session feel? | Heart-rate percentage, RPE, talk test (ACSM, England Athletics) | Maximal-heart-rate formulas vary between individuals; RPE needs practice |
| Where is my threshold? | Laboratory or field threshold testing; RPE 7–8 "comfortably hard" | Threshold moves with training and fatigue; one test is not permanent |
| What might I run at another distance? | Race-prediction tools and power-law formulas | Error grows with distance gap; hills, weather and tactics are not in the formula |
| What exact pace per kilometre? | Coaching systems (VDOT, McMillan and others) | Systems disagree; error is larger for beginners and recreational runners |

A practical approach: use heart rate and perceived effort to decide how hard today should be, then take a **range** from a pace table rather than a single point; start near the slower end and only move toward the faster end after 2–3 sessions completed with good recovery. The site's [heart-rate zones](/en/articles/heart-rate-zones/) and [race-prediction tool](/en/tools/race-predict/) are more useful together than a pace table alone.

## An example: one 10 km result, two different tables

Suppose a runner enters a 10 km time of 45 minutes into two tools. Both return easy, threshold and interval ranges, but the boundaries, names and workout categories differ; a session one tool calls "stamina" may be called "threshold" by the other. This page deliberately does not reproduce the exact seconds, because doing so would turn one commercial system into "the standard".

A sensible approach: treat the overlap of the two ranges as the commonly acceptable area; check it against RPE and the talk test — easy running should allow full conversation, threshold running only short answers; if the table's "easy" pace makes conversation impossible, it is not easy for you today. Tables are references; the body is the check.

## Common myths

- **"Pace tables are official standards."** They are not. ACSM and England Athletics give heart rate, RPE and relative race pace, not percentage pace tables; the seconds come from coaching systems.
- **"Two calculators disagree, so one is wrong."** More likely they use different assumptions and fits. VDOT tables and the online calculator differ by about 10 seconds over 5 km, and the Riegel exponent is used as both 1.06 and 1.07732.
- **"VDOT equals laboratory VO₂max."** Scudamore's study shows it underestimates, with a larger error in recreational runners.
- **"If the table says threshold pace, that is my threshold."** Threshold moves with training, fatigue, terrain and temperature; one test is not permanent.
- **"Beginners should copy elite zones."** The systems are fitted to and assume trained runners; error is larger for beginners and returning runners.
- **"Pace zones replace heart rate and feel."** They cross-check each other; they do not replace each other.

## Checklist

- [ ] Which system am I using, and what are its zone names and boundaries?
- [ ] Was my input a maximal race or a training estimate?
- [ ] How far is that distance from my goal distance? Could the error be amplified?
- [ ] Does the table's "easy" pace actually allow full conversation?
- [ ] Am I treating zones as ranges and starting from the slower end?
- [ ] Will I recalculate after 4–8 weeks instead of reusing an old table?

## Scope and limits

This page is training education. It provides no personal pace prescription and endorses no commercial system. Pace tables suit trained, uninjured runners in mild conditions; beginners, runners returning from injury, pregnant people, people with cardiovascular or metabolic disease and anyone training in heat or at altitude should be assessed by a qualified coach or clinician first. No pace recommendation replaces immediate action for pain, dizziness, chest pain or unusual breathlessness.

## Slopes and pace zones

Pace zones distort on gradients. The same “marathon pace” uphill may already be threshold effort, while downhill may fall below easy. Correct with [grade-adjusted pace](/en/knowledge/grade-adjusted-pace-method/) before reading heart rate and breathing; do not transplant flat zones onto the mountain.

## Related reading

- [Lactate Threshold and VO₂max Testing: Definitions, Error and Practical Use](https://learn.paobu.org/en/articles/lactate-threshold-and-vo2max-testing/)
- [Pace calculator](https://tools.paobu.org/en/tools/pace/)
- [Split table](https://tools.paobu.org/en/tools/splits/)
- [Grade-adjusted pace](https://tools.paobu.org/en/tools/grade-adjusted-pace/)

## Sources and verification date

- ACSM, Tips for Monitoring Aerobic Exercise Intensity: moderate 65%–75% HRmax, vigorous 76%–96% HRmax, RPE 3–4/5–7, talk test and step rate; no race-derived percentage pace table.
- England Athletics, Simplifying the running jargon: Training pace (2024-04-25): easy 60%–75% HRmax and RPE 2–3, threshold RPE 7–8, intervals about 3K–10K race pace; no percentage pace table.
- Jack Daniels, Daniels' Running Formula, 4th ed. (Human Kinetics, 2022, ISBN 9781718203662): the VDOT system and training paces, a coaching method rather than an official standard.
- McMillan Running, Using Your Training Paces: four training zones, pace ranges and heart-rate/RPE labels; described as estimates, recalculated every 4–8 weeks.
- Scudamore et al., An Evaluation of Time-Trial-Based Predictions of VO₂max and Recommended Training Paces, J Strength Cond Res 2018: VDOT underestimates VO₂max, error about 4.7%/9.2%, interval and threshold paces differ by ability level.
- Blödorn and Döring, Special endurance coefficients enable the evaluation of running performance, Sci Rep 2025: VDOT tables and the online calculator differ by about 10 seconds over 5000 m; Riegel exponent 1.07732 versus 1.06.

Verification date: 2026-11-07.

<!-- related-ring -->
## Related entries

- [Training volume progression — the 10% rule, the 30% ceiling and a workable framework](/en/knowledge/training-volume-and-progression/)
- [A weekly running week: easy runs, quality and the long run](/en/knowledge/training-week/)
- [Ultramarathon basics: what 100 km really asks](/en/knowledge/ultra-running-basics/)
