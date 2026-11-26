---
entityId: tool:race-qualifier-checker
locale: en
title: "Race qualifier checker: compare your result against the official standard, buffer and missing conditions"
summary: "Enter target event type, sex category, age on race day, qualifying result and course certification. The tool looks up the official standard, computes the buffer in minutes, returns an eligibility verdict, a missing-condition code and a rule note. It does not replace the current edition's entry rules, qualifying-window review or official result recognition."
aliases: ["Race qualifier checker", "qualifier checker", "marathon qualifying time lookup"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool calculates, and when not to use it

For entry into results-gated races such as the Boston Marathon, two questions matter: which age-sex standard your finish matches, and whether that result counts. This tool combines event type, sex category, age on race day, recent finish time and course certification to look up the official standard, calculate the buffer in minutes, return an eligibility verdict, a missing-condition code and the rule wording: meeting the standard only opens an application, and when the field is capped faster applicants may still be cut; a qualifying result must come from an officially published, certified course, and GPS, watch or Strava recordings are not accepted.

It suits marathon runners who already have an official finish and want to check the gate for a target race, and those who work backward from a standard to set training goals. It does not suit three situations. First, you have no official race result and want to use a training run or fitness recording as qualification. Second, the current edition revised the standard table, window or age category while you still hold the old version. Third, you need to check whether the result date falls inside the entry qualifying window; this tool does not verify dates, and that must be confirmed against the current rules. The tool implements standards visible on 2026-11-25; future editions may revise them.

## Inputs and units

Result time is in minutes; age is taken on race day; event and sex are dropdown categories; course certification is a yes/no flag.

| Input | Unit | Required | Range and notes |
| --- | --- | --- | --- |
| `event` | enum | Yes | `boston` Boston Marathon, `comrades` Comrades Marathon |
| `sex` | enum | Yes | `M` men, `F` women |
| `ageOnRaceDay` | years | Yes | Age on race day, 18–90 |
| `qualifyingTimeMinutes` | min | Yes | Qualifying finish, 1–600 min |
| `qualifierCourseCertified` | boolean | Yes | Whether the qualifier course is certified |

Note that age is on race day, not registration day; enter the official net chip time rather than gun time; course certification means the course holds a valid International Course Measurement Certificate, with start–finish separation and elevation drop checked in the certification. A trail race, treadmill or uncertified road race does not qualify for these events even with a faster time.

## Formula, assumptions and rounding

The tool validates event, sex, age, result and certification ranges first, then looks up the standard by event.

- Boston: age on race day falls into the official age group; `M` takes the men's standard, `F` takes the women's standard.
- Comrades: open category, one standard of 300 minutes (official limit 4:59:59; this gate rounds to 5:00:00).
- Buffer = standard minutes − qualifying minutes, rounded to the whole minute; positive means faster than standard, negative means slower.
- Eligibility: certification flag true and qualifying time ≤ standard; otherwise eligible is false.
- Missing condition: uncertified course → `certified-course`; certified but slower than standard → `time`; both satisfied → `null`.
- Rule note: at Boston meeting the standard only opens an application, and a capped field is cut by time; Comrades accepts only officially published results from compliant races, not GPS, Strava or watch splits.

Main assumptions: the entered result is a net chip time on an officially published, certified course; the tool applies standards in force on 2026-11-25, which later editions may revise; it does not check whether the result date sits inside the acceptance window; age is classified on race day by the official group boundaries. Buffer rounds to the whole minute; standards and results stay in whole minutes.

## How to read the results

The result area shows standard minutes, buffer, eligibility verdict, missing-condition code and rule note.

| Output | Meaning | How to use it |
| --- | --- | --- |
| Qualifying standard | Official gate in minutes for the age-sex group | Compare with your best official result |
| Buffer | Standard minus result; positive is margin, negative shortfall | A thin buffer leaves little training headroom |
| Eligible | Combined certification and time verdict | When false, check the missing condition first, then the time gap |
| Missing condition | `certified-course`, `time` or `null` | An uncertified course does not count however fast the time |
| Rule note | Application cap and result-source wording | Read the current regulation before entering |

Note that eligibility is not the same as acceptance. Boston's accepted field is capped, and qualifiers faster than the basic standard can still be cut; a three-minute buffer is not safe, because next year's standard may move and your result may vary. When the course is uncertified, the tool returns eligible false and records `certified-course`, even if the result number beats the standard; when the course is certified but the result is slower, the missing condition is `time`. The Comrades open standard does not split by age or sex, but the minimum age on qualification day is 20, and the result must come from a compliant race of at least 42.2 km; per the specification this tool accepts 18–90, and the age-floor wording follows that edition's FAQ.

## Case one: typical

Boston, `M`, 32 on race day, qualifying time 172 minutes (2:52), course certified.

| Item | Calculation | Result |
| --- | --- | --- |
| Standard | 18–34 men | 175 min (2:55:00) |
| Buffer | 175 − 172 | 3 min |
| Missing condition | Certified and meets standard | `null` |
| Verdict | 172 ≤ 175 and certified | Eligible |

The result beats the men's standard by three minutes with certification complete, so the verdict is eligible. That three minutes is only a margin against the standard: when Boston's field is capped, the cutoff can sit faster than the basic standard; if the result came from a net-downhill course or outside a valid measurement certificate, its validity still follows BAA rules.

## Case two: boundary

Comrades, `F`, 35, qualifying time exactly 300 minutes, course certified.

| Item | Calculation | Result |
| --- | --- | --- |
| Standard | Open category | 300 min |
| Buffer | 300 − 300 | 0 min |
| Missing condition | Certified and meets standard | `null` |
| Verdict | 300 ≤ 300 and certified | Eligible |

The result sits exactly on the standard with zero buffer, so the verdict is eligible. This boundary shows that equalling the standard qualifies without needing a few extra seconds; the official limit is 4:59:59, and this tool uses a 300-minute gate, so a right-on-the-line result should be confirmed against official timing before entry. The qualifier must be a compliant race of at least 42.2 km with an officially published result.

## Case three: invalid or missing input

First, age on race day 15 is below the 18 minimum; the tool rejects it as a range error before looking up any standard, with error field `ageOnRaceDay`. Second, result 0 or 700 minutes falls outside 1–600; an event or sex outside the table is rejected as an enum error. Third, the certification flag is empty or non-boolean; the tool handles it as a range error.

Fourth, the result comes from an uncertified course: the tool still computes standard and buffer, but eligible is false and the missing condition is `certified-course`; this is not a time gap but an unacceptable result source. Fifth, an empty browser age or result field yields a non-finite number; the tool treats it as a non-finite error rather than turning an empty string into zero for comparison.

## Relation to routes and knowledge

Result validity rests on course measurement and certification. A World Athletics certified road event holds an International Course Measurement Certificate issued by an approved measurer, valid for five years; certification checks start–finish separation, the allowed elevation drop and the measurement procedure itself; results from an expired or missing certificate cannot be used as certified results. This aligns with the course-certification principles in [records and course validity](/en/knowledge/records-and-course-validity/). Marathon distance and timing wording are in [marathon distance](/en/knowledge/marathon-distance/), and race-day rhythm in [race-day pacing](/en/knowledge/race-day-pacing/).

Read the two target profiles alongside: the [Boston Marathon](/en/routes/boston/) standard table splits by age and sex, and meeting it only opens application; the [Comrades Marathon](/en/routes/comrades-marathon/) requires officially published results from compliant races, with a window published per edition. The table in this tool comes from the official BAA qualifying page and the official Comrades FAQ; other results-gated races' gates are not included.

## Common failure modes and early signals

The first failure mode is treating a training run or watch recording as a qualifying result. Qualification recognizes only officially published finish records; GPS tracks, Strava splits and treadmill results do not substitute. Early signal: your best entered result has no race name, placement or official link.

The second is using the wrong age group or sex category. Near an age boundary or across categories, the standard group changes. Early signal: you compared against the previous age band, or the sex category is entered against the wrong table.

The third is ignoring certification. A fast result on an unmeasured, expired-certificate or over-dropped course is not accepted in qualification review. Early signal: the qualifier was a local altered half, a short trail loop or a neighbourhood out-and-back with no traceable measurement certificate number.

The fourth is treating meeting the standard as acceptance. The field cutoff can be faster than the basic standard, and qualifiers can still be turned away; runners with a thin buffer should train to a target inside the standard, not right on the line. Early signal: you compare a single recent best without allowing for result variation or a standard raise.

## Limits

The tool suits pre-entry checks against the Boston Marathon and Comrades Marathon official standards; it does not cover other results-gated races' gates, and it does not review entry windows, result dates, race placements or waitlist rules. It is not an entry promise; result validity, certification and qualification dates are ultimately determined by the organizing committee under the current regulation. When that edition's standard table, acceptance window or age category changes, the latest announcement on the race website governs.

## This change

2026-11-25: this tool and its three cases were created; the algorithm follows the R67 specification, the standard table comes from the official BAA qualifying page and the Comrades FAQ, and the course-certification wording from the World Athletics certified road events page. No existing route or knowledge body was rewritten in this round.

## Related reading

- [Records and course validity: measurement, certification and result conditions](/en/knowledge/records-and-course-validity/)
- [Marathon distance: course definition and timing wording](/en/knowledge/marathon-distance/)
- [Race-day pacing: organising first and second half rhythm](/en/knowledge/race-day-pacing/)
- [Boston Marathon route profile and qualifying standards](/en/routes/boston/)
- [Comrades Marathon route profile and entry requirements](/en/routes/comrades-marathon/)

## Sources and scope

The Boston age-sex table, minimum age 18, application-only nature and certified-course plus net-downhill adjustment rules come from the official BAA qualifying page. Compliant race distance, 4:59:59 limit, officially published result wording, minimum age 20 and window arrangement come from the official Comrades FAQ. The five-year measurement certificate, start–finish separation and drop checks, and non-recognition of expired-certificate results come from the World Athletics certified road events page. The minute conversion in the table, buffer arithmetic and missing-condition codes are this tool's implementation; the qualifying date window is not checked by the tool. Verified 2026-11-25. Not covered: other selection races' gates, that edition's cutoff placement and waitlist rules follow the race website.

<!-- related-ring -->
## Related entries

- [Pre-race taper plan: drop volume over two or three weeks, keep pace](/en/tools/taper-planner/)
- [Grade-adjusted pace — converting hill pace to flat-equivalent pace with the Minetti polynomial](/en/tools/grade-adjusted-pace/)
- [Heat pace adjustment: estimate a slowdown from temperature and humidity](/en/tools/heat-adjust/)
