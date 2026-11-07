---
entityId: "knowledge:core-terms"
locale: "en"
title: "Core running terms: pace, RPE, cadence and training language"
summary: "A shared glossary for pace, speed, RPE, easy running, tempo, intervals, long runs, taper, cadence, elevation gain, VO2max, lactate threshold, running economy, GPX and GeoJSON."
aliases: ["running glossary", "pace terms", "RPE", "cadence", "VO2max", "GPX", "GeoJSON"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## Definition and who this applies to

This page is a glossary: it defines recurring words in training plans, physiology and route files, with checkable units. It supports reading, not an exam answer or prescription.

It applies to runners and readers new to plans, route files or tool output. The condition: coaches, studies and devices may measure the same word differently, so comparisons must first establish definition, units and conditions.

## Pace, speed and average pace

- **Pace** is time per unit distance, usually minutes per kilometre or mile; smaller is faster.
- **Speed** is distance per unit time, usually km/h or m/s. Pace and speed are reciprocal, but 5 minutes 30 seconds per kilometre is not 5.3 kilometres per hour.
- **Average pace** is total time divided by distance; stops and climbs are averaged out.

## Effort and session types

- **RPE** is perceived exertion (often 0–10 or 6–20), personal and best cross-checked with the talk test. The CDC test: moderate means talking but not singing; vigorous means a few words before a breath.
- **Easy run**: full sentences are possible and you finish with something left.
- **Tempo run**: sustained “comfortably hard” work; intensity and duration vary.
- **Intervals**: repeated quality bouts with recovery, by time or distance.
- **Long run**: the week’s longer easy or endurance run, not a maximum test.
- **Taper**: a planned pre-race reduction; no universal number of days.

## Technique: cadence, stride, climb and grade

- **Cadence** is steps per minute. A review found higher stride rate at fixed speed reduced vertical excursion, ground reaction force and joint energy absorption; studies were small, so no universal target exists, and cadence varies with speed, gradient, height and fatigue.
- **Stride length** rises with speed; longer is not automatically better.
- **Elevation gain** is the sum of positive changes, not finish minus start.
- **Grade** is rise over horizontal distance, often a percentage. Uphill running has a higher step frequency and shorter aerial phase; downhill running has longer aerial time and lower step frequency.

## Physiological markers

VO2max, lactate threshold and running economy are widely studied determinants, but marathon performance is multi-factorial, including technological and cognitive factors. Measurements depend on protocol, so laboratory values and watch estimates are not interchangeable; threshold definitions also vary.

## Route files: GPX and GeoJSON

- **GPX** is an XML schema for GPS data; version 1.1 defines track, route and waypoint structures with latitude, longitude and optional elevation.
- **GeoJSON** is a JSON format for geospatial objects, including LineString. Coordinates use longitude, latitude order, and positions may include elevation.

## Quick reference table of terms and units

| Term | Definition | Usual unit | Watch out |
| --- | --- | --- | --- |
| Pace | Time per unit distance | min/km, min/mile | Smaller is faster |
| Speed | Distance per unit time | km/h, m/s | Reciprocal of pace |
| RPE | Perceived exertion | 0–10 or 6–20 | Personal; cross-check |
| Cadence | Steps per minute | steps/min | No universal target |
| Elevation gain | Sum of positive changes | metres | Not the net rise |
| Grade | Rise over horizontal distance | % | Read both directions |

## How to look up and apply a term in three steps

1. **Locate word and context.** Decide whether it describes speed, effort, technique, physiology or a file format.
2. **Check units and basis.** Copy the number and unit, then confirm distance basis, elevation and protocol.
3. **Verify with one independent figure.** Recalculate average pace or net rise; if it does not match, return to the source.

## Worked example: converting pace, speed and climb

Assume 42.195 kilometres in 4 hours 30 minutes at an even pace. Average pace is 270 ÷ 42.195, about 6 minutes 24 seconds per kilometre; speed is about 42.195 ÷ 4.5, or 9.38 kilometres per hour. Assume the route starts at 10 metres, finishes at 40 metres and records 120 metres of cumulative gain: the net rise is only 30 metres. A 1-kilometre segment rising 50 metres has a grade of about 5%. All figures are hypothetical.

## Reading a term in context

A term is shorthand for a measurement convention, and the convention matters as much as the word. Pace is time per distance, speed is distance per time, and a "5:00 pace" means five minutes per kilometre only if the distance unit is kilometres; the same number in miles describes a much faster runner. Elevation gain sums every upward metre, so a rolling loop accumulates more gain than its net change suggests. When a term appears without its unit or measurement method, treat the number as incomplete rather than guess.

Glossaries are most useful when read alongside a concrete session. Take one workout you know well, look up the three or four terms that describe it, and check whether your intuitive use matches the definition. That small exercise prevents most miscommunication in training plans and race briefings.

## Common pitfalls

- **Treating one cadence figure as a standard.** The review sets no universal target; a copied number ignores speed, gradient and height.
- **Taking a watch VO2max as a laboratory result.** Estimates and measured protocols are not interchangeable.
- **Confusing elevation gain with net rise.** Mixing bases misstates a route.
- **Using pace and speed as synonyms.** Convert units first.

## Review frequency and progression

An illustrative rhythm: if you read two training articles a week, review this page every 4–6 weeks, starting with pace, RPE, easy run, cadence and elevation gain, then add three terms each time. Progression means stating a number’s unit, basis and conditions.

## When to stop and seek help

Stop exercising and seek medical help for chest pain, fainting, unusual palpitations, persistent vomiting or marked breathlessness. Persistent or night pain deserves clinical assessment. A watch’s VO2max, recovery score or heart-rate alert is a prompt, not an examination, and should not change treatment alone.

## Lookup checklist

- [ ] The word is identified as speed, effort, technique, physiology or file format.
- [ ] Number, unit, distance basis and conditions are written down.
- [ ] One independent figure was recalculated and any difference explained.
- [ ] Research findings, advice and inference are kept separate.
- [ ] The original source was checked rather than stacking second-hand numbers.

## Scope and limits

This page does not provide an individual prescription, diagnosis or guarantee of device accuracy. VO2max and lactate-threshold values need qualified testing; pain, illness and medication questions belong with a professional.

## Related reading

- [A weekly running week: easy runs, quality and the long run](https://learn.paobu.org/en/articles/training-week/)
- [What easy running really means](https://learn.paobu.org/en/articles/easy-run/)
- [How to read running research: question first, conclusion later](https://learn.paobu.org/en/articles/reading-running-research/)

## Sources and scope

Intensity and the talk test follow the CDC; cadence and stride follow the Sports Health review; uphill and downhill follow the Sports Medicine review; the VO2max and running-economy framework follows the PubMed review; marathon distance follows World Athletics; GPX follows GPX 1.1; GeoJSON follows RFC 7946. Verified 2026-11-06.
