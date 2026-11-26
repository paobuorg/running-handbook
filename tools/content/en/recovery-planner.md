---
entityId: tool:recovery-planner
locale: en
title: "Post-race recovery planner — dates for walking, walk-run, easy running and quality"
summary: "Enter race date, distance, age and strength training to get recovery days, walk-run, continuous-run, quality and race-ready dates plus a phase table. Date arithmetic only, not medical clearance."
aliases: ["赛后恢复规划器", "recovery planner", "复跑日期", "恢复表"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool solves

The most common question after a race is “when can I run again”. Guesses tend to two extremes: a hard session on day three because it feels fine, or six weeks of fear. This tool turns race distance, age and strength training into a dated recovery table: when walk-run starts, when continuous easy running starts, when quality work returns and when the body is race-ready.

It does dates, not diagnosis. Pain, swelling, abnormal urine or palpitations are red flags outside the formula; they need clinical care.

## Inputs and outputs

Four inputs: race date (YYYY-MM-DD), race distance (5k/10k/half/marathon/50k/100k/100mi), age on race day (18–80) and whether strength training is included. Outputs are recovery days, walk-run start, continuous run date, quality start, race-ready date, strength start and a dated phase table.

Dates count from the day after the race; race day is not recovery day one. Everything runs locally in the browser and is not uploaded.

## Formula and rounding

```
recoveryDays = distanceBase + ageExtra
walkRunDay = max(3, ceil(recoveryDays × 0.35))
continuousDay = max(walkRunDay + 2, ceil(recoveryDays × 0.60))
qualityDay = recoveryDays
readyDay = recoveryDays + 7
strengthDay = walkRunDay if strength else continuousDay
```

Distance base: 5k/10k 7 days, half 10, marathon 14, 50k 21, 100k 28, 100mi 42. Age extra: 40–49 +2, 50–59 +4, 60+ +7. All fractions round up so the plan never shortens recovery.

## Input ranges

| Input | Range | Meaning |
|---|---|---|
| Race date | real calendar date | must parse as YYYY-MM-DD |
| Race distance | seven options | sets the base |
| Age | 18–80 | sets the extra days |
| Strength training | yes/no | sets the strength start |

Out-of-range values raise an error rather than silently clipping. Invalid dates such as 30 February also fail.

## Case one: marathon on 2026-11-29, age 47, strength included

| Item | Calculation | Result |
|---|---|---|
| Recovery days | 14 + 2 | 16 days |
| Walk-run starts | day 6 | 2026-12-05 |
| Continuous run | day 10 | 2026-12-09 |
| Quality starts | day 16 | 2026-12-15 |
| Race-ready | day 23 | 2026-12-22 |

In plain terms: walking only before 5 December; walk-run until 9 December; easy continuous running until 15 December; only after 22 December consider another race.

## Cases two and three

| Scenario | Recovery days | Walk-run | Continuous | Quality | Race-ready |
|---|---|---|---|---|---|
| 5k on 2027-01-23, age 32 | 7 | 01-26 | 01-28 | 01-30 | 02-06 |
| 100 mi on 2027-08-28, age 58 | 46 | 09-14 | 09-25 | 10-13 | 10-20 |

The 5k table is short, but short does not mean intensity is allowed; quality still waits until day seven. The 100-mile table is nearly seven weeks, and no “back on the mountain in week three” plan fits it.

## Age and distance boundaries

The age extra is a conservative buffer, not a medical finding. Tendon and fascia repair slows after 40, and sleep and recovery are more easily disrupted after 50, but individual variation is large. Judge by pain, gait, morning resting heart rate and sleep, not the table alone.

The distance bases are also conservative: there are real jumps between 50k and 100k, and between 100k and 100mi. With exceptional climb, heat or a pre-race injury, push the whole table back 1–2 weeks.

## How this differs from the four-week guide

| Need | Use |
|---|---|
| Concrete dates | this tool |
| Weekly content, nutrition and sleep | [four-week recovery guide](/en/knowledge/four-week-post-race-recovery-plan/) |
| Review after a withdrawal | [DNF review](/en/knowledge/dnf-review-protocol/) |
| Scheduling the next race | [race calendar planner](/en/tools/race-calendar-planner/) |

The tool gives the date skeleton; the guide gives the content. A complete plan passes both.

## Pain red flags

The table does not handle red flags. Pause and seek care for night pain at rest, unilateral swelling and heat, morning stiffness over 30 minutes, arch or heel tenderness lasting a week, abnormal urine, palpitations or persistent low fever.

Do not mask pain with analgesics to stay on the table. The schedule assumes no symptoms; it is not a task list to complete through symptoms.

## Common mistakes

One: treating recovery days as complete rest days. The period includes walking and walk-run, not lying down. Two: jumping to continuous running on day three because it feels fine. Three: returning to pre-race intensity in week four. Four: using a 30-year-old table at 50.

Five: watching dates but not gait and pain. Six: starting strength during the walking phase. Seven: back-calculating recovery from the next race instead of the next race from recovery.

## Chinese runners and 40+

Most races are on Sunday and work resumes Monday. Split week-one walking into commute plus lunch, rather than forcing one 40-minute block; put strength in the evening instead of a rushed morning.

Over 40 with knee alignment, lumbar or Achilles history should have a clinician or physio review the table before pushing the walk-run date back another week. The table is a generic start, not a personal prescription.

## Checklist

Before input: confirm date, distance, age and strength choice. After output: put the four dates in the calendar; review pain, sleep and resting heart rate every Sunday; stop on any red flag.

Do not enter the next race before recovery is complete; the entry date should be later than the race-ready date, not equal to it.

## Related reading and tools

Read the [four-week recovery guide](/en/knowledge/four-week-post-race-recovery-plan/) for weekly content; read [post-race recovery](/en/knowledge/post-race-recovery/) for physiology; use the [race calendar planner](/en/tools/race-calendar-planner/) to fit recovery into the next race.

For 100k/100mi, read the route page for climb and cut-offs before deciding whether to shift the table.

## How to use the table

Put the four dates straight into the calendar: walk-run, continuous run, quality and race-ready. Attach a condition check to each: 30 minutes pain-free, no next-day swelling, pain-free down stairs, 20 symmetrical single-leg calf raises. If the condition fails, move the date; do not force the calendar.

Review four metrics every Sunday: morning resting heart rate, sleep, pain 0–10 and gait. If two worsen, step back a phase instead of waiting until running is impossible. The table is a map, not a contract.

## Connecting to the next plan

After recovery, do not bolt on the old twelve-week race plan. Spend 1–2 weeks of easy running back to 60–70% of pre-race volume, then start the next build; the first week of that plan should be easier than the end of recovery, not harder.

If the next race is fixed, send the race-ready date to a coach or crew so training is scheduled around it, not back-calculated from the race.

## Sources and verification boundary

The day ranges draw on NHS running-injury return guidance, ISSN protein and nutrient-timing consensus, and sleep/recovery research; sources and claims are in the entity JSON. This is not a clinical pathway and does not replace a doctor or physiotherapist.

Last verified: 2026-11-26. Next review trigger: sports-medicine return-to-run guidance, distance-base changes, age-extra evidence.

