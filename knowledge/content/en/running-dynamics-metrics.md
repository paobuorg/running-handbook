---
entityId: knowledge:running-dynamics-metrics
locale: en
title: "Ground Contact Time and Vertical Oscillation: What the Numbers Can and Cannot Tell You"
summary: "Checking Garmin's public documentation, wearable validation studies and a review of running biomechanics confirms that no medical society or official body publishes a threshold for 'bad' ground contact time. This page explains how the metrics are measured, how much devices disagree, why correlation with performance is not causation, and why the numbers should not be used to prescribe gait changes."
aliases:
  - ground contact time
  - vertical oscillation
  - vertical ratio
  - running dynamics
  - GCT
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## Definitions and scope

**Ground contact time (GCT)** is the duration of one step during which the foot is in contact with the ground, measured in milliseconds. **Vertical oscillation (VO)** is the up-and-down movement of the torso while running, measured in centimetres. **Vertical ratio** is vertical oscillation divided by stride length, expressed as a percentage. All three are estimated from accelerometers and gyroscopes; none is measured directly.

This page asks a narrower question: what can these numbers actually tell you? It is written for runners who see the metrics on a watch and do not know what to do with them. It does not provide a gait-retraining plan, and it does not treat manufacturer ranges as medical or coaching standards.

## Verification result: manufacturer ranges only, conflicting research

Checking whether any official body publishes a decision threshold gives three findings:

- **No threshold exists.** Sports-medicine reviews and society documents do not use ground contact time or vertical oscillation as prescription targets. There is no citable rule such as "over X milliseconds is poor" or "above Y centimetres is excessive".
- **Manufacturers publish descriptive ranges.** Garmin's public pages state that elite runners are often under 200 ms and that virtually all experienced runners are under 300 ms, while also noting that faster paces often come with somewhat higher vertical oscillation. These are observations, not pass marks.
- **The research is contradictory.** A review of running economy classifies the GCT–economy relationship as equivocal: some studies find no relationship, some find longer contact times more economical, and some find the opposite.

The position of this page is therefore: **definitions, measurement differences, and not a basis for prescription.** Current evidence does not support using these numbers to direct gait change.

## What official sources and manufacturers actually say

| Source | What it provides | What it does not provide |
|---|---|---|
| Garmin, Ground Contact Time | Definition; elite often **<200 ms**, virtually all experienced runners **<300 ms**; longer contact time linked to overstriding | No threshold for "poor", no standard stratified by age, level or pace |
| Garmin, Vertical Oscillation | Measured at the torso in centimetres; more experienced runners tend to be lower; faster paces often produce **slightly higher** oscillation | No normal range, no "how much improvement is enough" |
| Garmin, Vertical Ratio | Oscillation ÷ stride length; a low ratio is described as a small cost for a large benefit | No threshold, no performance-prediction formula |
| Sports Medicine review (Moore 2016) | Lower vertical oscillation may improve running economy, but evidence is limited and methodologically weak | No general "economical technique" prescription |

## How the numbers are produced

- **Wrist watches** estimate from wrist accelerometers. Arm swing is related to torso motion, but it is not the same measurement.
- **Running dynamics pods** sit at the lower back and measure torso movement.
- **Foot sensors** sit on the shoe or ankle and are closest to the actual contact event.
- **Laboratory systems** use force plates as the gold standard, defining contact start and end by a force threshold; 3D motion capture can substitute, but algorithms differ between studies.

The same runner on the same run gets a different set of numbers when the sensor moves.

## How large the measurement differences are: four verifiable figures

| Comparison | Difference | Conditions |
|---|---|---|
| Garmin Running Dynamics Pod vs force plate + 3D motion capture | Bias of **−81.5 ± 18.4 ms** at the fastest step rate; significantly different at all three rates (n=11, p<0.001) | Running in place, not normal forward running |
| Torso IMU vs instrumented treadmill | Bias **−29 ms**, precision 20 ms | Validation studies cited in the review |
| Torso IMU vs force plate | Bias **4.6 ms**, precision 12.1 ms | Same review |
| Accelerometer vs force plate | Accelerometer readings **14.6 ± 0.5% longer** | Treadmill; the difference arose mainly in the later, force-free part of contact |

These figures do not mean every device is inaccurate. They mean that **milliseconds from different products, mounting positions and algorithms cannot be compared with each other, and cannot be checked against a laboratory threshold.**

## Speed sets the number: read the pace before the milliseconds

- In the studies reviewed, contact time falls as speed rises: about **310 ms** at 2.9 m/s, **210 ms** at 4.7 m/s and **140 ms** at 7.8 m/s; about **104 ms** in elite sprinters at maximal speed.
- Laboratory measurement at 2-hour marathon pace: contact time **160 ± 10 ms**, vertical oscillation **4.0 ± 0.6 cm**.
- "My contact time is 250 ms" therefore means nothing unless pace, gradient, shoe and device are stated.

## Correlation is not causation: contact time and running economy

The 2016 review is explicit: the evidence on contact time and running economy is **equivocal**. Several studies found no relationship; some found longer contact times associated with better economy; others found shorter ones. The proposed explanations run in both directions: very short contacts require rapid force production and recruit metabolically expensive fast-twitch fibres, while long contacts extend the braking phase. What may matter more than duration is **how much speed is lost during contact**.

The evidence for vertical oscillation is no stronger. The review lists lower oscillation among factors that appear beneficial, but notes that only one study had specifically manipulated it, so neither an "optimal" amplitude nor a guaranteed benefit can be established. It also notes that female runners have lower oscillation than males while findings on economy differences are conflicting.

A useful inference: **elite runners have short contact times because they run fast and produce high forces, not because short contact times made them elite.** Treating a cross-sectional difference as a training cause is the most common misuse of these metrics.

## Vertical oscillation and vertical ratio: why "lower is better" has conditions

Garmin's own statements complete each other: more experienced runners tend to have lower oscillation, yet faster paces often come with slightly higher oscillation. Both can be true, which means oscillation is not monotonically "lower is better"; it varies with speed, stride length, height and running style.

Vertical ratio offsets part of the speed effect by dividing oscillation by stride length, but it still depends on an estimated stride length produced by the same algorithm. It describes a broad trend; it cannot grade a single session.

## Changing the metric is not improving the outcome

Adams 2018 had 20 active runners complete three conditions: baseline, higher cadence, and a cue to reduce vertical oscillation. All three metrics were calculated with Garmin Connect's proprietary algorithm.

- **Higher cadence**: contact time fell **4.7%**; average vertical loading rate fell **21.2%**, instantaneous vertical loading rate fell **16.0%**, and braking impulse decreased significantly.
- **Lower oscillation cue**: contact time actually rose **3.5%**; average vertical loading rate fell **33.4%**, instantaneous vertical loading rate also fell (p=0.001), and peak vertical ground reaction force fell more markedly.
- Conclusion: both cues reduced loading rates linked to injury risk, but **only higher cadence reduced braking impulse**; the study did not measure performance or running economy.

In other words, **a metric changing and performance changing are two different events.** Making the number look better may change a different variable than the one you intended.

## What the metrics are and are not for

| Appropriate | Not appropriate |
|---|---|
| Long-term trends: same device, same pace, same terrain, over weeks | Comparing absolute values across devices or paces |
| Supporting evidence alongside RPE, sleep and pain | Judging "good or bad form" from one reading |
| One-variable experiments under a coach, with other metrics recorded | Treating manufacturer ranges as a prescription or pass mark |
| Interpreting alongside pace, stride length and heart rate | Making "lower contact time" the training goal |

For cadence and stride length, see [cadence and stride length](https://learn.paobu.org/en/articles/cadence-and-stride/). For putting wearable data into recovery decisions, see [wearables and recovery data](https://learn.paobu.org/en/articles/wearables-and-recovery-data/).

## A worked example

A runner at 5:00/km sees a contact time of 260 ms and a vertical oscillation of 9 cm on a wrist watch and worries it is "bad". A reasonable reading order is:

1. **Confirm the device and mounting position**: wrist watch, pod or foot sensor.
2. **Note the pace and terrain**: uphill, trail and headwind all change the values.
3. **Compare with the same device at the same pace over the past 6–8 weeks**, not with someone else's absolute numbers.
4. **Only then ask**: is there pain, is recovery affected, is race performance affected?

A single 260 ms reading supports no conclusion. Garmin's public page only says virtually all experienced runners are under 300 ms; it does not say 260 ms is a problem.

## Common misconceptions

- **"Shorter contact time is always better"**: the economy evidence is inconsistent, and the value depends strongly on speed.
- **"Lower vertical oscillation is always better"**: the manufacturer itself says faster paces often produce higher oscillation, and only one study manipulated oscillation.
- **"The watch and the laboratory measure the same thing"**: mounting position and algorithm differ; the Garmin pod deviated by −81.5 ms while running in place.
- **"Elite values are target values"**: a cross-sectional difference is not a training cause.
- **"Better numbers mean the training worked"**: in Adams 2018, the low-oscillation cue made contact time longer.
- **"These metrics predict injury"**: the studies measured loading-rate surrogates, not the metrics themselves.

## Checklist

- [ ] Which device am I using, and where is it worn?
- [ ] What were the pace, gradient and surface for this reading?
- [ ] Am I comparing with my own past on the same device, or with someone else's absolute value?
- [ ] Did I look at RPE, pain and recovery alongside the number?
- [ ] Have I turned a manufacturer range into a pass mark?
- [ ] If changing gait, am I working with a qualified coach and changing one variable at a time?

## Limits of this page

This page is training education. It does not diagnose gait, prescribe retraining or endorse any device. The metrics are only useful as trends measured on the same device under the same conditions. Pain, injury or cardiovascular symptoms should be addressed clinically rather than by adjusting numbers. Stop and seek medical care if chest pain, dizziness, unusual breathlessness or a steadily worsening pain appears during training.

## Sources and verification date

- Garmin, Ground Contact Time: definition; elite often under 200 ms and experienced runners under 300 ms; overstriding linked to longer contact time; no decision threshold.
- Garmin, Vertical Oscillation: measured at the torso in centimetres; more experienced runners tend to be lower; faster paces often slightly higher; no normal range.
- Garmin, Vertical Ratio: oscillation ÷ stride length; low ratio described as small cost for large benefit; no threshold.
- Drobnič et al., The Validity of a Three-Dimensional Motion Capture System and the Garmin Running Dynamics Pod…, Sensors 2023: 11 participants running in place; significant differences at all step rates, with a −81.5 ± 18.4 ms bias for the pod at the fastest rate; cited IMU biases of −29 ms, 4.6 ms and 13 ms; contact time values across speeds; each 1% increase in asymmetry associated with 3.7% higher metabolic cost.
- Weyand et al., Ambulatory estimates of maximal aerobic power from foot-ground contact times and heart rates in running humans, J Appl Physiol 2001: accelerometer readings 14.6 ± 0.5% longer than force plate, mainly in the later contact phase.
- Physiological demands of running at 2-hour marathon race pace, J Appl Physiol 2020: contact time 0.16 ± 0.01 s, vertical oscillation 0.04 ± 0.006 m, peak vertical force 2.92 ± 0.26 body weights.
- Moore, Is There an Economical Running Technique? A Review of Modifiable Biomechanical Factors Affecting Running Economy, Sports Med 2016: equivocal contact-time evidence; limited vertical-oscillation evidence with only one manipulation study; caution against general technique prescriptions.
- Adams et al., Altering Cadence or Vertical Oscillation During Running: Effects on Running Related Injury Factors, Int J Sports Phys Ther 2018: 20 runners; high cadence reduced contact time by 4.7%, average vertical loading rate by 21.2% and instantaneous vertical loading rate by 16.0%; the low-oscillation cue increased contact time by 3.5% and reduced average vertical loading rate by 33.4%; performance and economy were not measured.

Verified on 2026-11-07.
