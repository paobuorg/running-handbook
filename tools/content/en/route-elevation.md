---
entityId: tool:route-elevation
locale: en
title: "Route elevation: a local GPX elevation profile"
summary: "Read GPX or GeoJSON and calculate distance, ascent, descent, elevation range and maximum grade, with a downsampled profile. Missing elevation stays unknown rather than becoming zero."
aliases: ["route elevation", "elevation profile", "GPX climb"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool does

Choose a local GPX or GeoJSON file and the tool reads the track in your browser, calculates total distance, cumulative ascent, cumulative descent, minimum and maximum elevation, and the largest absolute grade between adjacent points, then draws an elevation profile. It is for runners checking the shape of a route before setting out, comparing training routes, or reviewing the elevation in an activity. It is not course certification, a safety assessment or navigation. If elevation is unreliable, or the official gain figure matters, use the event's published data rather than treating one GPX total as certified.

## Calculation rules and grade definition

| Output | Rule | Unit and handling |
| --- | --- | --- |
| Distance | Sum of WGS84 geodesic distances between consecutive points per segment | Metres, whole |
| Ascent | Sum of all positive elevation differences | Metres, whole |
| Descent | Sum of absolute negative differences | Metres, whole |
| Minimum/maximum elevation | Lowest and highest valid elevations | Metres, one decimal |
| Maximum grade | Δelevation ÷ horizontal distance × 100% | Percent, one decimal, absolute value |
| Profile | Downsampled to at most 160 points | Distance whole metres, elevation two decimals |

Segments are calculated separately; their endpoints are not joined artificially. Grade is computed only for pairs with at least 5 metres of horizontal distance, to avoid amplifying noise from very close samples. Maximum grade is therefore a point-pair estimate, not a road-design grade or the average difficulty of a whole climb.

## Worked example

Assume three points: `[0, 0, 0]`, `[0, 0.001, 100]`, `[0, 0.002, 0]`, moving about 111.19 metres in latitude.

| Output | Hand calculation |
| --- | --- |
| Ascent | 0→100 is +100 m; 100→0 adds none: 100 m |
| Descent | 100→0 is −100 m: 100 m |
| Elevation range | 0 m to 100 m |
| Maximum grade | 100 ÷ 111.19 × 100% ≈ 89.9%, shown as 89.9% |
| Profile points | 3 valid points, below the 160 cap, all kept |

These values follow independent arithmetic. If any adjacent point lacks elevation, ascent, descent and the profile should be unknown rather than calculated from only the complete pairs.

## Rounding and tolerance

Distance, ascent and descent round to the nearest whole metre with a ±0.5 m tolerance. Elevation keeps one decimal with ±0.05 m; grade keeps one decimal with ±0.05 percentage points; profile points use whole-metre distance and two-decimal elevation. GPS elevation drifts, and devices, barometers and correction methods produce different totals, so displayed precision is not real accuracy. Compare routes from the same source and elevation basis where possible.

## Reading the result

Read total distance and the scale of climbing first, then look for steep rises, steep drops and long climbs in the profile, alongside aid points, surface and weather. “Unknown” elevation means the data is missing, not that the route is flat. When only some points have elevation, the tool returns unknown with an incomplete-coverage warning instead of undercounting ascent. Maximum grade describes one adjacent pair; it does not give the average difficulty of a climb or replace judgments about technical terrain, traffic or rockfall.

## How to use it

1. Export a GPX or GeoJSON with elevation from the watch or app, and confirm it is line geometry with elevation fields.
2. Open it locally and read distance, ascent, descent, elevation range and maximum grade, then inspect the profile for key steep sections.
3. If elevation is missing or partial, repair the source or use official elevation data; when comparing routes, keep one source and basis.

## Limits and when not to use it

Elevation is used as recorded and GPS elevation is noisy. Segments are measured independently and endpoints are not joined. Grade is a point-pair estimate, not a smoothed road-design grade. Files are read locally. The tool does not certify the course or assess surface, technicality or safety. It is not suitable for deciding whether a course is official, permitted or race-ready, or for inferring finish time from maximum grade.

## When this number misleads you

Elevations are used exactly as supplied, and GPS elevation is noisy; over short distances a few metres of jitter becomes a very large point-to-point grade. Segments are measured independently and endpoints are not joined, so a multi-segment file understates total distance. A simplified track has had points and their elevations deleted, which usually lowers the gain. The same route recorded by a barometric watch, a phone and another watch can produce materially different gain figures.

Do not use it to certify official gain, rank course difficulty, predict finish times or assess permits, and do not treat it as safety advice.

## Related reading

- [Uphill and downhill running: pace, form and cost](https://learn.paobu.org/en/articles/uphill-and-downhill/)
- [Trail navigation: tracks, maps and backups](https://learn.paobu.org/en/articles/trail-navigation/)

## Privacy and data

The file is parsed locally and not uploaded; results are not saved after the page closes. Oversized or malformed files produce an error rather than a partial result. Check whether the start reveals a home address before sharing.

## Sources and scope

File boundaries follow the public GPX and GeoJSON specifications; distance and geodesy follow WGS84; uphill and downhill mechanics follow sports-biomechanics reviews. Elevation comes from the file itself. Verified 2026-11-06.
