---
entityId: tool:grade-adjusted-pace
locale: en
title: "Grade-adjusted pace — converting hill pace to flat-equivalent pace with the Minetti polynomial"
summary: "Enter the average gradient and the pace you actually ran, and convert it into the flat pace with the same modelled metabolic cost using the Minetti et al. (2002) running-cost polynomial. It is an equal-cost conversion, not a performance prediction, and it does not replace coaching or medical judgement."
aliases: ["grade adjusted pace", "GAP", "hill pace conversion"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool is for

Six minutes per kilometre uphill and six minutes per kilometre downhill are not the same physiological cost. This tool combines gradient and actual pace into one comparable number: it first computes the metabolic cost at that gradient, then converts it into the **flat pace with the same modelled metabolic cost** (grade-adjusted pace, usually shortened to GAP). It is useful for comparing the training load of different routes, recording the true intensity of a climb, or separating "I ran slowly today" from "today's route was hilly".

It does not predict race performance, and it does not tell you how fast you "should" be able to run on the flat. The flat-equivalent pace answers "what flat pace would carry the same metabolic cost", not "what is my ability". Fitness, fatigue, altitude, temperature, wind, surface and tactics are all outside the formula.

## Formula and range rules

Gradient is expressed as a percentage: `i = gradient (%) / 100`, positive uphill and negative downhill. Running cost uses the fifth-order polynomial fitted by Minetti et al. (2002) to treadmill running, in joules per kilogram per metre (J/kg/m):

```
Cr(i) = 155.4·i⁵ − 30.4·i⁴ − 43.3·i³ + 46.3·i² + 19.5·i + 3.6
```

The flat cost (i = 0) is the constant 3.6 J/kg/m. The cost ratio and the conversion are:

```
cost ratio = Cr(i) / 3.6
flat-equivalent pace = actual pace / cost ratio
```

Uphill, Cr is above 3.6 and the ratio is above 1, so the flat-equivalent pace is a smaller number of seconds (faster). On a moderate descent, Cr is below 3.6 and the ratio is below 1, so the flat-equivalent pace is a larger number (slower). The valid range is −45% to +45%, matching the treadmill gradients in the original study.

For an actual pace of 5:00 per kilometre (300 seconds per kilometre):

| Gradient | Cost (J/kg/m) | Relative to flat | Flat-equivalent pace |
|---|---|---|---|
| −30% | 2.462 | 0.684 | 7:19 per km (439 s) |
| −20% | 1.800 | 0.500 | 10:00 per km (600 s) |
| −10% | 2.152 | 0.598 | 8:22 per km (502 s) |
| −5% | 2.746 | 0.763 | 6:33 per km (393 s) |
| 0% | 3.600 | 1.000 | 5:00 per km (300 s) |
| +5% | 4.685 | 1.301 | 3:51 per km (231 s) |
| +10% | 5.968 | 1.658 | 3:01 per km (181 s) |
| +20% | 9.007 | 2.502 | 2:00 per km (120 s) |
| +30% | 12.579 | 3.494 | 1:26 per km (86 s) |

The table also exposes a counter-intuitive part of the model: downhill cost is lowest near −20%, and becomes higher again on steeper descents (−30% already costs more than −20%). That is the shape of the polynomial, not a claim that steeper descents are easier. Real downhill running also involves braking, impact absorption and eccentric muscle damage.

## Worked cases

**Case one (uphill)**: actual pace 360 seconds per kilometre (6:00 per km), gradient +8%.

| Item | Calculation | Result |
|---|---|---|
| Gradient as a fraction | 8 / 100 | 0.08 |
| Cost | 155.4×0.08⁵ − 30.4×0.08⁴ − 43.3×0.08³ + 46.3×0.08² + 19.5×0.08 + 3.6 | 5.43342 J/kg/m |
| Ratio | 5.43342 / 3.6 | 1.50928 |
| Equivalent pace | 360 / 1.50928 | 238.53 → 239 s/km (3:59 per km) |

**Case two (downhill)**: actual pace 300 seconds per kilometre (5:00 per km), gradient −10%.

| Item | Calculation | Result |
|---|---|---|
| Gradient as a fraction | −10 / 100 | −0.10 |
| Cost | 155.4×(−0.10)⁵ − 30.4×(−0.10)⁴ − 43.3×(−0.10)³ + 46.3×(−0.10)² + 19.5×(−0.10) + 3.6 | 2.1524 J/kg/m |
| Ratio | 2.1524 / 3.6 | 0.59789 |
| Equivalent pace | 300 / 0.59789 | 501.77 → 502 s/km (8:22 per km) |

Both cases can be checked by hand. Note the direction: the uphill flat-equivalent pace is faster than the actual pace, while the downhill flat-equivalent pace is slower.

## Rounding and precision

Cost is shown to three decimal places, the ratio to three decimal places, and the equivalent pace to the nearest whole second, so the pace tolerance is 1 second and the cost and ratio tolerance is 1e-6. Rounding happens only at the end: the equivalent pace is computed from the unrounded ratio, avoiding cumulative error.

The inputs have their own precision limits. A watch estimates gradient from barometric pressure or GPS, and instantaneous gradient on a short segment can be very noisy; course elevation profiles also carry metre-level errors. Use an average over at least several hundred metres rather than a single reading. The model assumes a constant gradient across the segment, while real courses change continuously.

## Reading the result

- **Uphill**: the equivalent pace is faster, meaning the same actual pace cost more on the climb. Use it to judge whether a climb has approached threshold intensity, not as a speed you can hold on the flat.
- **Moderate descent**: the model treats the descent as cheaper, so the equivalent pace is slower. Eccentric load and braking are not in the formula, and the steeper the descent, the less the number should be trusted on its own.
- **Steep descent (below roughly −25%)**: the modelled cost stops falling and may rise, but that does not mean the descent is safer or harder in reality; it means the polynomial no longer represents the real cost there.
- **Comparing routes**: record both actual and equivalent pace for each segment to see the true intensity distribution of a route instead of being led by total ascent.
- **Not for race prediction**: the equivalent pace is not an equivalent result. Racing also depends on glycogen, hydration, heat, altitude, eccentric damage from descents and tactics.

## How to use it

1. Pick a segment with a fairly even gradient. Record its distance, ascent or average gradient, and the average pace in seconds per kilometre.
2. Enter the actual pace and the average gradient, then read the cost, the ratio and the flat-equivalent pace.
3. Write the equivalent pace into your training log and compare it with the same route over time, not with someone else's flat pace.
4. If the gradient is beyond ±20%, treat the result as a rough reference and combine it with perceived effort, heart rate and how the legs feel after the descent.

## Limits

This tool is for steady running on roads, tracks and gentle hills. It does not apply to routes that need ropes, snow or technical terrain, or to run-walk, intervals and segments with rapidly changing gradient. It does not replace coaching, race strategy or medical advice; runners with an injury, cardiovascular disease, or training in heat or at altitude should address those larger variables first. The tool does not calculate when the gradient is outside −45% to +45%, when pace is zero or negative, or when an input is not finite.

The model comes from ten elite mountain runners on a treadmill: a small sample in a controlled setting. It cannot represent every population, surface or fatigue state. Downhill eccentric damage, braking, technical difficulty and psychological cost are outside the model. A biomechanics review adds that uphill running uses a higher step frequency and shorter flight phase, while downhill running has longer flight, more rear-foot striking and relies on eccentric work and energy dissipation (knowledge-uphill-downhill-running); no single polynomial captures all of that.

## When this number misleads you

The model comes from ten elite mountain runners on a treadmill and holds only for steady running at a constant gradient between −45% and +45%. Real courses change gradient continuously; the shorter the segment, the more GPS elevation noise inflates a local grade into a big percentage and makes segment-by-segment GAP jump around. Downhill does not include braking, eccentric damage or technical difficulty, so a faster flat-equivalent pace does not mean you can actually run that fast downhill. Altitude, heat, wind, surface and body mass are outside the model.

Do not use it to predict finish times, to rank trail difficulty or to prescribe training intensity. Extrapolating across distance or terrain adds error rather than cancelling it.

## Related reading

- [Uphill and downhill running: pace, form and cost](https://learn.paobu.org/en/articles/uphill-and-downhill/)
- [Training pace zones: how to set and use them](https://learn.paobu.org/en/articles/training-pace-zones/)

## Sources and scope

The fifth-order running-cost polynomial, the −0.45 to +0.45 gradient range, the flat cost of 3.6 J/kg/m and R² = 0.99 come from Minetti, Moia, Roi, Susta and Ferretti in the Journal of Applied Physiology (2002). The conversion "equivalent pace from the cost ratio" is the method this site applies to that polynomial; it is not a race-result formula from the original paper. The paper measured steady-state metabolic cost on a treadmill and says nothing about predicting race performance.

The biomechanical differences between uphill and downhill running (step frequency, flight time, rear-foot striking and eccentric work) come from the review "Biomechanics and Physiology of Uphill and Downhill Running" (knowledge-uphill-downhill-running); they describe the model's limits and are not used in the calculation.

This article and tool were verified on 2026-11-07.
