---
entityId: tool:training-load
locale: en
title: "Acute-to-chronic load ratio: review the last 7 days against 28 days"
summary: "Enter weekly training minutes, sessions, average perceived exertion and the 7-day and 28-day loads to get an acute:chronic ratio, weekly change and an experience-based band. It is a review prompt, not a diagnosis, and evidence on load and injury is conflicting."
aliases: ["Acute-to-chronic load ratio: review the last 7 days against 28 days", "training load", "ACWR"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What the tool is for

Training load is one of the most quantified and most misread parts of running. This tool compares the last 7 days with the 28-day average, then labels the result low, typical, elevated or spike. It is for runners who already keep a training log and want to review recent tempo before adding volume, to see whether the week continues the routine, enters a planned reduction, or jumps upward.

It does not predict injury. A systematic review of 36 studies and 23,047 runners found that 26.2% reported a running-related injury, but evidence linking weekly distance, duration, frequency, intensity or recent changes to injury was conflicting, and the authors caution against recommending one optimal progression for every runner. The bands here are therefore experience-based heuristics, not a diagnosis, and they do not replace observing the body's own signals.

## Inputs and outputs

There are five inputs: weekly training minutes, sessions per week, average perceived exertion (1–10), the 7-day load and the 28-day average load. The first three check the record basis and provide context; they do not enter the ratio. The last two are the numerator and denominator. Outputs are the acute:chronic ratio, the weekly change percent, the load band and a plain-language note. The ratio answers how recent load compares with the 28-day average; the weekly change answers how many percent it rose or fell; the band only maps the ratio onto four experience-based prompts. The tool outputs neither an injury probability nor a training prescription.

## Formula and load basis

The ratio is computed only when the 28-day average load is greater than zero:

- Acute:chronic ratio = 7-day load ÷ 28-day average load
- Weekly change = (7-day load − 28-day average) ÷ 28-day average × 100

Loads need one consistent method. The page uses a common convention: session load ≈ duration in minutes × perceived exertion (1–10), summed over the period. That convention is an experience-based heuristic, not the only valid method. If you normally track load by heart-rate zones or distance, you may keep your own method, but the 7-day and 28-day periods must use the same method; otherwise numerator and denominator are not comparable.

## Band rules

| Band | Ratio | Weekly change | Prompt |
| --- | --- | --- | --- |
| Low | below 0.8 | usually negative | Check for a recovery week or missing records |
| Typical | 0.8 to 1.3 inclusive | roughly −20% to +30% | Recent load is close to the average |
| Elevated | above 1.3 up to 1.5 | above +30% to +50% | Review sleep, pain and recovery |
| Spike | above 1.5 | above +50% | Review training before adding more |
| Undefined | 28-day average is 0 | no value | Enter a 28-day average first |

The 0.8, 1.3 and 1.5 cut-offs and rules of thumb such as "10% progression" come from training practice, not diagnostic thresholds in the cited review. The evidence itself is conflicting, so the band only helps organise a review; it cannot settle a conclusion on its own.

## Worked example 1: typical band

With a 7-day load of 420 and a 28-day average of 400:

| Item | Calculation | Result |
| --- | --- | --- |
| Ratio | 420 ÷ 400 | 1.05 |
| Weekly change | (420 − 400) ÷ 400 × 100 | +5.0% |
| Band | 1.05 lies between 0.8 and 1.3 | typical |

This means recent load is roughly level with the 28-day average, a weekly change of about +5%. It does not prove the plan is optimal; it only shows the two periods are close to the routine under one matching method.

## Worked example 2: the 1.50 upper boundary

With a 7-day load of 600 against the same 400 average, the ratio is 600 ÷ 400 = 1.50 and the change is (600 − 400) ÷ 400 × 100 = +50.0%. Exactly 1.50 remains at the top of the elevated band; only above 1.5 is a spike. Boundary values are inclusive, so rounding cannot produce a "1.50 displayed but spike" contradiction. This case checks where the cut-off sits; it is not advice to push load toward the boundary.

## Worked example 3: spike band

With a 7-day load of 720 and a 28-day average of 400: ratio 720 ÷ 400 = 1.80, weekly change (720 − 400) ÷ 400 × 100 = +80.0%, band spike. The matching inputs are 360 minutes this week, 5 sessions and average RPE 7; these are context only and do not change the ratio. The spike prompt is to hold volume for a week and check sleep, pain, recovery and upcoming racing before adding more; it is neither an injury diagnosis nor a rest prescription.

## Boundary case: 28-day average of zero

When the 28-day average load is zero, the ratio and weekly change are undefined and the band is unknown. This usually happens when records are just starting, several days are missing, or the recording method has changed. In that situation, zero should not be treated as a stable reference: build at least one full period of log before comparing the two loads. The tool returns no value rather than an infinite or empty ratio.

## Rounding and precision

The ratio keeps two decimals and the change one decimal; the band uses the rounded ratio, so a displayed value cannot disagree with its band. Tolerance is 1e-6 and there is no integer rounding. The reliability of the result rests on the recorded load: if the 28-day log has gaps, the ratio is systematically over- or under-estimated, and rounding cannot remove that error. When recomputing by hand, keep unrounded intermediate values before applying the rounding rules.

## Reading the result

A typical band means recent load is near the 28-day average, not that the plan is sound. Elevated or spike does not prove injury; it invites a look at recovery, sleep, pain and upcoming racing. A low band may be a planned recovery week or an incomplete log. Persistent fatigue and a performance decline should prompt consideration of overtraining syndrome and exclusion of underlying illness; that assessment is clinical, with no single diagnostic marker, and includes rest plus correcting the imbalance between training and recovery.

## Common pitfalls

The first pitfall is treating the ratio as an injury probability: the band is a heuristic with conflicting evidence, and it cannot predict whether injury will occur. The second is mixing load methods: RPE, heart-rate and distance approaches must not be split across the 7-day and 28-day periods. The third is reading a low ratio as under-training; it may equally be a planned recovery week or missing records. The fourth is trusting the ratio over the body: sleep, pain, mood and performance often flag problems before a number does.

## Limits

The tool suits runners with a consistent training log. It does not suit children, pregnant runners, runners in rehabilitation or anyone needing clinical assessment. It does not replace clinical assessment of overtraining syndrome, nor judge whether a single session is safe. Evidence linking load to injury is conflicting, and no band can serve as permission to add load or as evidence of injury. The public-health baseline of at least 150 minutes of moderate activity per week plus two strength sessions is a different level of measure from this load ratio. Persistent fatigue, an unusually high resting heart rate, recurring pain or a sustained performance decline should lead you to a medical or sports professional.

## How to use it

1. Record 7-day and 28-day loads with one method, checking for gaps.
2. Enter weekly minutes, sessions, average perceived exertion and both loads.
3. Interpret with sleep, pain and the next few weeks; after a large rise, hold volume before adding more.

## Related reading

- [Load and overtraining: signals and limits](/en/knowledge/load-and-overtraining/)
- [Volume progression: how much and how fast](/en/knowledge/training-volume-and-progression/)
- [Running pain, load and when to seek help](/en/knowledge/pain-and-load/)
- [Training log: what to record and how to review it](/en/knowledge/training-log/)
- [Periodization: base, peak and taper](/en/knowledge/periodization/)

## Sources and scope

The injury proportion, conflicting evidence and caution against one optimal progression come from the review of 36 studies and 23,047 runners. Overtraining syndrome, the fatigue assessment, the absence of a single diagnostic marker, and rest plus correction of the imbalance come from a practical overtraining guide. The 150-minute and two-strength-day baseline comes from CDC guidance. The ratio cut-offs, session-load convention and 10% advice are experience-based heuristics not found in those sources. Verified 2026-11-26.

<!-- related-ring -->
## Related entries

- [Crew and pacer plan: schedule handoffs against the official access list](/en/tools/crew-pacer-plan/)
- [Cutoff buffer planner: check each checkpoint against the official cutoff table](/en/tools/cutoff-planner/)
- [Race checklist: generated by surface, duration and weather](/en/tools/race-checklist/)
