---
entityId: knowledge:heart-rate-zones
locale: en
title: "How to Set Heart Rate Zones — reserve, formula error and self-checking"
summary: "Heart rate zones convert a relative intensity into beats per minute. Two conventions are common: percentage of maximal heart rate (%HRmax) and percentage of heart rate reserve (%HRR). Using the ACSM 8th-edition bands of 40–59% and 60–84% HRR, the Tanaka 2001 equation 208 − 0.7 × age, and the HERITAGE error figures (12.4 bpm for Fox, 11.4 bpm for Tanaka in 762 people), this guide derives the conversion between the two conventions, provides age-and-resting-rate zone tables, three worked examples, a talk-test check, and a step-by-step method for recalculating zones when a watch's numbers do not hold up. It is exercise-physiology education, not a diagnosis."
aliases: ["heart rate zones", "heart rate reserve", "HRR", "Karvonen formula", "max heart rate formula", "zone 2 running"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## Definitions and scope

A **heart rate zone** is not a gear on your heart; it is a relative intensity converted into beats per minute (bpm). Two conventions are common on this site:

- **%HRmax**: a percentage of maximal heart rate, for example "run at 70% of max heart rate".
- **%HRR (heart rate reserve, also called the Karvonen method)**: first compute `HRR = HRmax − HRrest`, then `target = %HRR × HRR + HRrest`.

The ACSM 8th edition defines **moderate intensity as 40–59% HRR** (roughly 64–76% HRmax) and **hard (vigorous) intensity as 60–84% HRR**. This page uses only those two official bands; it does not invent five-zone or seven-zone cut points.

This page is for: runners who want a defensible boundary between easy and hard days; runners whose "220 − age" zones never feel right; runners who wonder why two platforms report different zones.

It is **not** for: people taking medication that changes heart rate responses (for example beta blockers), people with a known arrhythmia or a pacemaker, people who are feverish or fighting an infection, or anyone treating zones as a diagnostic tool. Those readings cannot be interpreted with these formulas; follow the intensity advice from your clinician.

## Formulas and derivation

Let `age` be age, `HRrest` resting heart rate and `HRmax` maximal heart rate.

1. Maximal heart rate estimate (Tanaka 2001): `HRmax ≈ 208 − 0.7 × age`.
2. Heart rate reserve: `HRR = HRmax − HRrest`.
3. Target heart rate: `target = %HRR × HRR + HRrest`.

Expand step 3:

```
target = %HRR × (HRmax − HRrest) + HRrest
       = HRmax × [%HRR × (1 − HRrest/HRmax) + HRrest/HRmax]
```

The bracketed term is the equivalent %HRmax:

```
equivalent %HRmax = %HRR × (1 − r) + r, where r = HRrest / HRmax
```

The derivation shows one important thing: **the conversion between %HRR and %HRmax depends on your own resting heart rate**, not on a fixed constant. The ACSM table's "40–59% HRR ≈ 64–76% HRmax" holds at its reference population's resting level; when your resting rate differs, the two columns stop matching.

## How far apart are the two conventions?

Take age 40. Tanaka gives `HRmax = 208 − 0.7 × 40 = 180 bpm`. Keep 40% and 59% HRR fixed and change only the resting rate:

| Resting HR | HRR | 40% HRR target | 59% HRR target | Equivalent %HRmax (40% / 59%) |
|---|---:|---:|---:|---|
| 50 | 130 | 102 | 127 | 56.7% / 70.4% |
| 60 | 120 | 108 | 131 | 60.0% / 72.7% |
| 70 | 110 | 114 | 135 | 63.3% / 74.9% |

The ACSM %HRmax column is fixed at 64–76%, which converts to 115–137 bpm at this max. A runner with a resting rate of 50 therefore gets a moderate band of 102–127 bpm from %HRR — 10–13 bpm lower than the %HRmax column. A runner at 70 gets 114–135, which is closer. **Mix the two conventions and low-resting-rate runners train systematically too easy, while high-resting-rate runners train too hard.**

All bpm values in this table are computed from the formula and rounded to whole beats; they are not measurements.

## Estimating max heart rate: Tanaka versus 220 − age

The Tanaka, Monahan and Seals (2001) meta-analysis collected group mean maximal heart rates from **351 studies, 492 groups and 18,712 subjects**. Maximal heart rate was strongly related to age (**r = −0.90**) with the regression `208 − 0.7 × age`. A laboratory cross-validation in **514 healthy subjects** produced `209 − 0.7 × age`, virtually identical to the meta-analysis; the regression did not differ between men and women and was not affected by wide variation in habitual activity.

The same paper states that the older `220 − age` equation **underestimates maximal heart rate in older adults**. Computing both equations shows the direction:

| Age | 220 − age | 208 − 0.7 × age | Difference |
|---:|---:|---:|---:|
| 30 | 190 | 187 | 220 − age is 3 higher |
| 60 | 160 | 166 | 220 − age is 6 lower |

These rows are direct calculations, not measurements. The older the person, the larger the underestimate from the old equation — which is why Tanaka recommended the newer one.

## How large is the error? Put numbers on it

Formulas are population regressions, not individual measurements. Sarzynski et al. (2013) compared both equations against laboratory-measured maximal heart rate in **762 sedentary HERITAGE subjects**. The standard error of estimate (SEE) was:

| Equation | Whole sample SEE | White | Black | Female | Male |
|---|---:|---:|---:|---:|---:|
| Fox (220 − age) | **12.4 bpm** | 11.0 | 14.4 | 12.3 | 12.6 |
| Tanaka (208 − 0.7 × age) | **11.4 bpm** | 10.2 | 13.1 | 11.2 | 11.7 |

The paper also notes that the Fox formula's SEE is usually **7–12 bpm**, and that Tanaka reported a SEE of about **10 bpm**. The authors concluded that age-based equations **do not precisely predict an individual's measured maximal heart rate**.

How to read this: SEE is the scale of the error, not a guaranteed maximum. Two people of the same age and sex commonly differ by more than ten beats, and sometimes by more than twenty. Treating the formula value as an exact ceiling shifts the whole zone. **If you will use zones for hard training, get a verifiable max-heart-rate or threshold test when you can; when you cannot, treat the formula band as a starting point and calibrate with the talk test and perceived effort.**

## How to measure resting heart rate

In the HERITAGE sample, resting heart rate was **65.4 bpm (standard deviation 9.1)**, with individual values from **40.3 to 105.3 bpm**. That spread means "resting 60 is normal" is not a rule; you need your own number.

Method (this is practical advice, not a research finding):

1. **Timing**: on waking, before getting up, or after urinating and sitting quietly for 5 minutes. Do not use a reading after a run, after coffee or tea, or after a poor night's sleep.
2. **Same position**: lying or seated, same time of day, every time.
3. **Count a full 60 seconds**: use a pulse or a chest strap. Wrist optical sensors can wobble at low rates, so confirm once by pulse.
4. **Average several days**: record 3 consecutive days and average; discard a day when you are ill, dehydrated or sleep-deprived.
5. **Do not substitute "lowest overnight rate"**: the watch's overnight minimum means something different from morning resting rate, and plugging it into the formula overestimates HRR.

## A table by age and resting heart rate

Using `HRmax = 208 − 0.7 × age`, `HRR = HRmax − HRrest`, resting rate 60 bpm, rounded to whole beats:

| Age | HRmax | HRR | Moderate 40–59% HRR | Hard 60–84% HRR |
|---:|---:|---:|---|---|
| 30 | 187 | 127 | 111–135 | 136–167 |
| 40 | 180 | 120 | 108–131 | 132–161 |
| 50 | 173 | 113 | 105–127 | 128–155 |
| 60 | 166 | 106 | 102–123 | 124–149 |

If your resting rate is not 60, recalculate with the next section. Per 10 bpm of resting-rate difference, the same percentage moves the target by 6 bpm at 40%, 4 bpm at 59% and 1.6 bpm at 84% (computed from the formula).

## Three worked examples

**Example 1: age 35, morning resting 52 bpm**

- `HRmax = 208 − 0.7 × 35 = 183.5`
- `HRR = 183.5 − 52 = 131.5`
- Moderate lower `0.40 × 131.5 + 52 = 104.6 → 105`
- Moderate upper `0.59 × 131.5 + 52 = 129.6 → 130`
- Hard lower `0.60 × 131.5 + 52 = 130.9 → 131`
- Hard upper `0.84 × 131.5 + 52 = 162.5 → 162`

**Example 2: age 48, morning resting 68 bpm**

- `HRmax = 174.4`, `HRR = 106.4`
- Moderate `111–131`; hard `132–157`

**Example 3: age 60, morning resting 58 bpm**

- `HRmax = 166`, `HRR = 108`
- Moderate `101–122`; hard `123–149`

Enter these into the watch rather than letting it generate zones from "220 − age". Most watches let you override max and resting heart rate; do that before choosing manual zones.

## Checking with the talk test

The CDC rule is: at **moderate intensity you can talk but not sing**; at **vigorous intensity you cannot say more than a few words without pausing for a breath**. Compare that with both ends of your zones:

- Near the moderate lower bound, you should be able to say a full sentence. If speech is already strained, the band is too high.
- Near the moderate upper bound, speech becomes broken but still forms sentences. If you cannot speak at all, you are already hard.
- Near the hard upper bound, only a few words come out. If you can chat comfortably there, the formula's ceiling is too low.

When formula, watch and talk test disagree, **trust the talk test and perceived effort first, then check the formula inputs** (age, resting rate, overnight-minimum substitution). The talk test is a rule of thumb and cannot separate fine sub-zones, but it reliably catches "the whole band is too high or too low".

## Recalculating when the watch's zones are wrong

Work through this in order; it usually takes about ten minutes:

1. **Check the watch's HRmax setting.** If it shows "220 − age", replace it with `208 − 0.7 × age`, or with a measured value if you have one.
2. **Check where resting heart rate comes from.** Confirm it is a morning resting value; if it is the overnight minimum or a post-run reading, replace it with the method above.
3. **Compute HRR yourself**: `HRmax − HRrest`, and note it down.
4. **Set two bands**: moderate `0.40 × HRR + HRrest` to `0.59 × HRR + HRrest`; hard `0.60 × HRR + HRrest` to `0.84 × HRR + HRrest`.
5. **Create manual zones in the watch.** Most watches let you set bpm limits; avoid "automatic percentage of max heart rate".
6. **Validate on two runs**: one easy run (should sit in the moderate band with full sentences), one tempo run (should sit in the hard band with short phrases). Adjust by the talk test if the mismatch exceeds 5 bpm.
7. **Review every 6–8 weeks**: resting rate moves with training and sleep; the estimated max only changes with age, while a measured max can be retested yearly.

Steps 6 and 7 are practical advice, not research findings. The research establishes that formula error exists; it does not set a universal retest interval.

## Common misuses

- **Treating 220 − age as a measured max.** Its SEE is 7–12 bpm and 12.4 bpm in the HERITAGE sample; using it for a hard ceiling multiplies the error across the whole band.
- **Mixing %HRmax and %HRR.** The two differ by 10–13 bpm when resting rate is away from the reference level, as the worked table shows.
- **Using the wrong resting rate.** Overnight minimum, post-coffee or post-run readings over- or under-estimate HRR.
- **Assuming different platform zones mean a broken watch.** Platforms use different equations and cut points, and sometimes different names for the same band; inspect the inputs before comparing numbers.
- **Replacing perceived effort with zones.** Drift, heat, dehydration and poor sleep change what a given heart rate means; zones are one input, not a command.
- **Prescribing by formula for people on rate-changing medication.** Beta blockers and similar drugs lower heart rate, so formula bands no longer represent actual intensity.
- **Treating a zone as a medical judgement.** Abnormal heart rate is judged by symptoms and duration, not by whether it crossed an arbitrary band.

## When to stop or seek medical care

NHS guidance: palpitations are common and usually not serious, and can be triggered by strenuous exercise, lack of sleep, stress, medicines, alcohol, caffeine, nicotine or recreational drugs; some people get them during the menopause. **See a GP if palpitations keep coming back or get worse, last longer than a few minutes, or occur with a heart condition or a family history of heart problems.** **Call emergency services or go to A&E if palpitations occur with chest pain, shortness of breath, or feeling faint or fainting.**

In running terms: chest pain, a sense of impending doom or near-fainting → stop immediately and get help; an abnormal, persistent racing heart that does not settle after several minutes of rest → stop and seek care; a heart rate simply higher than expected while speech and symptoms are normal → check weather, hydration, caffeine and sleep first, then adjust intensity.

## Scope and boundaries

This page is exercise-physiology education. It does not provide diagnosis, treatment or medication advice. The formulas and error figures come from healthy adult samples and do not transfer directly to people on rate-changing medication, people with arrhythmias or pacemakers, pregnancy, or acute illness. Every bpm band here is a calculated result, not a measurement of you; when precise intensity matters, use a verifiable test and have it interpreted by a qualified professional.

Reviewed 2026-11-07.

## Related reading

- [heart-rate-drift](https://learn.paobu.org/en/articles/heart-rate-drift/)
- [Lactate Threshold and VO₂max Testing: Definitions, Error and Practical Use](https://learn.paobu.org/en/articles/lactate-threshold-and-vo2max-testing/)
- [easy-run](https://learn.paobu.org/en/articles/easy-run/)
- [Training pace zones: official guidance, coaching systems and what can be verified](https://learn.paobu.org/en/articles/training-pace-zones/)

## Sources

- ACSM's Guidelines for Exercise Testing and Prescription, 8th edition: HRR definition, moderate 40–59% HRR (about 64–76% HRmax), hard 60–84% HRR, target heart rate formula.
- Tanaka, Monahan and Seals, Age-predicted maximal heart rate revisited (J Am Coll Cardiol, 2001): 351 studies / 492 groups / 18,712 subjects, r = −0.90, 208 − 0.7 × age, cross-validation 209 − 0.7 × age in 514 subjects, no sex or activity-level difference, 220 − age underestimates in older adults.
- Sarzynski et al., Measured maximal heart rates compared to commonly used age-based prediction equations in the HERITAGE Family Study (Am J Hum Biol, 2013): 762 subjects, Fox SEE 12.4 bpm, Tanaka SEE 11.4 bpm, subgroup values, Fox 7–12 bpm, Tanaka about 10 bpm, resting heart rate 65.4 (SD 9.1, 40.3–105.3).
- CDC, How to Measure Physical Activity Intensity: moderate means can talk but not sing, vigorous means only a few words before a breath, talk test is a rule-of-thumb method.
- NHS, Heart palpitations: common and usually not serious, triggers, when to see a GP, when to call emergency services.
