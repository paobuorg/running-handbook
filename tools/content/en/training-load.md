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

Training load is one of the most quantified and most misread parts of running. This tool compares the last 7 days with the 28-day average, then labels the result low, typical, elevated or spike.

It does not predict injury. A systematic review of 36 studies and 23,047 runners found that 26.2% reported a running-related injury, but evidence linking weekly distance, duration, frequency, intensity or recent changes to injury was conflicting, and the authors caution against recommending one optimal progression.

## Formula and bands

- Acute:chronic ratio = 7-day load ÷ 28-day average load
- Weekly change = (7-day load − 28-day average) ÷ 28-day average × 100

Loads need one method. The page uses session load ≈ duration in minutes × perceived exertion (1–10), summed over the period. That convention is an experience-based heuristic, not the only valid method; distance or heart-rate-based loads work if both periods match.

| Band | Ratio | Weekly change | Prompt |
| --- | --- | --- | --- |
| Low | below 0.8 | usually negative | Check for a recovery week or missing records |
| Typical | 0.8 to 1.3 inclusive | roughly −20% to +30% | Recent load is close to the average |
| Elevated | above 1.3 up to 1.5 | above +30% to +50% | Review sleep, pain and recovery |
| Spike | above 1.5 | above +50% | Review training before adding more |
| Undefined | 28-day average is 0 | no value | Enter a 28-day average first |

The 0.8, 1.3 and 1.5 cut-offs are training-practice rules of thumb, not thresholds from the cited review.

## Worked example

With a 7-day load of 420 and a 28-day average of 400:

| Item | Calculation | Result |
| --- | --- | --- |
| Ratio | 420 ÷ 400 | 1.05 |
| Weekly change | (420 − 400) ÷ 400 × 100 | +5.0% |
| Band | 1.05 lies between 0.8 and 1.3 | typical |

With a 7-day load of 600 against the same 400 average, the ratio is 1.50 and the change +50.0%. Exactly 1.50 remains at the top of the elevated band; only above 1.5 is a spike.

## Rounding and precision

The ratio keeps two decimals and the change one decimal; the band uses the rounded ratio, so a displayed value cannot disagree with its band. Tolerance is 1e-6 and there is no integer rounding.

## How to read the result

A typical band means recent load is near the 28-day average, not that the plan is sound. Elevated or spike does not prove injury; it invites a look at recovery, sleep and pain. A low band may be a planned recovery week or an incomplete log. Persistent fatigue and a performance decline should prompt consideration of overtraining syndrome and exclusion of underlying illness; that assessment is clinical and includes rest plus correction of the imbalance.

## How to use it

1. Record 7-day and 28-day loads with one method, checking for gaps.
2. Enter weekly minutes, sessions, average perceived exertion and both loads.
3. Interpret with sleep, pain and the next few weeks; after a large rise, hold volume before adding more.

## Limits

The tool suits runners with a consistent training log. It does not suit children, pregnant runners, runners in rehabilitation or anyone needing clinical assessment.

## When this number misleads you

Acute and chronic load must use the same session-load definition; mixing RPE-based and heart-rate-based records makes the ratio meaningless. With incomplete records the 28-day average is underestimated and the ratio inflates; conversely, a planned recovery week produces a low ratio. The 0.8, 1.3 and 1.5 thresholds are experience-based, and the evidence linking load to injury is itself conflicting.

Do not use it to diagnose overtraining syndrome, to judge whether a single session is safe, or as permission to add load; persistent fatigue, performance decline or mood change need clinical assessment. It is not medical advice.

## Related reading

- [Load and overtraining: signals and limits](https://learn.paobu.org/en/articles/load-and-overtraining/)
- [Volume progression: how much and how fast](https://learn.paobu.org/en/articles/training-volume-and-progression/)
- [Running pain, load and when to seek help](https://learn.paobu.org/en/articles/pain-and-load/)

## Sources and scope

The injury proportion, conflicting evidence and caution against one optimal progression come from the review of 36 studies and 23,047 runners. Overtraining syndrome, the fatigue assessment, the absence of a single diagnostic marker, and rest plus correction of the imbalance come from a practical overtraining guide. The 150-minute and two-strength-day baseline comes from CDC guidance. The ratio cut-offs, session-load convention and 10% advice are experience-based heuristics. Verified 2026-11-07.
