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

Choose a local GPX or GeoJSON file and the tool reads the track in your browser, calculates total distance, cumulative ascent, cumulative descent, minimum and maximum elevation, and the largest absolute grade between adjacent points, then draws an elevation profile. It is for runners checking the shape of a route before setting out, comparing training routes, or reviewing the elevation in an activity after a run. The tool works from the geometry and elevation recorded in the file itself; it does not connect to a server or regenerate elevation for you. It is not course certification, a safety assessment or navigation. If elevation is unreliable, or the official gain figure matters, use the event's published data rather than treating one GPX total as certified.

## What it calculates: inputs and outputs

The only input is a local track file, in GPX or GeoJSON format, containing a point sequence with coordinates and optional elevation fields. The outputs are total distance, cumulative ascent, cumulative descent, minimum elevation, maximum elevation, maximum absolute grade, and a downsampled list of profile points. Distance and ascent answer how long the route is and how much up-and-down it contains; the elevation range answers from what height to what height you travel; maximum grade answers how steep the steepest adjacent pair is; the profile shows where climbs, descents and long gradients sit along the route. These metrics are direct statistics of the file geometry. They do not include pace, heart rate or a subjective difficulty score.

## Formula and calculation basis

| Output | Rule | Unit and handling |
| --- | --- | --- |
| Distance | Sum of WGS84 geodesic distances between consecutive points per segment | Metres, whole |
| Ascent | Sum of all positive elevation differences | Metres, whole |
| Descent | Sum of absolute negative differences | Metres, whole |
| Minimum/maximum elevation | Lowest and highest valid elevations | Metres, one decimal |
| Maximum grade | Δelevation ÷ horizontal distance × 100% | Percent, one decimal, absolute value |
| Profile | Downsampled to at most 160 points | Distance whole metres, elevation two decimals |

Segments are calculated separately; their endpoints are not joined artificially. Grade is computed only for pairs with at least 5 metres of horizontal distance, to avoid amplifying noise from very close samples. Maximum grade is therefore a point-pair estimate, not a road-design grade or the average difficulty of a whole climb.

## How to prepare the input

When exporting, prefer the raw track with elevation from the watch or running app, rather than a screenshot or route image. The GPX `ele` field and the GeoJSON elevation property determine whether elevation statistics can be computed; if barometer or elevation correction was disabled during export, the file may contain coordinates only. A multi-leg trip, an out-and-back route or a merged record may be stored as several segments, and the tool reads them segment by segment. When comparing two routes, use the same device, elevation source and export basis where possible; otherwise the difference in gain reflects recording method more than the route itself.

## Worked example 1: a typical undulating route

Assume three points: `[0, 0, 0]`, `[0, 0.001, 100]`, `[0, 0.002, 0]`, moving about 111.19 metres in latitude.

| Output | Hand calculation |
| --- | --- |
| Ascent | 0→100 is +100 m; 100→0 adds none: 100 m |
| Descent | 100→0 is −100 m: 100 m |
| Elevation range | 0 m to 100 m |
| Maximum grade | 100 ÷ 111.19 × 100% ≈ 89.9%, shown as 89.9% |
| Profile points | 3 valid points, below the 160 cap, all kept |

These values follow independent arithmetic, not the page script's own output. The horizontal distance per pair is estimated from a latitude step near the equator; at other latitudes the WGS84 geodesic distance applies, so the magnitude matches but the exact figure shifts slightly.

## Worked example 2: missing elevation as a boundary case

When the elevation of an adjacent pair is null, missing or blank, ascent, descent and the profile all return unknown rather than being computed against a zero elevation. This is a deliberate conservative treatment: treating missing elevation as zero reads the route as flat and systematically undercounts gain. The tool likewise returns unknown when elevation covers only some points, with an incomplete-coverage warning. The criterion is whether a valid elevation difference exists; a file with complete coordinates but missing elevation is still a boundary case and should not produce a definite gain number.

## Worked example 3: separate segments are not joined (common pitfall)

Assume the file holds two independent segments: segment A is `[0, 0, 0] → [0, 0.001, 50]` and segment B is `[0, 0.003, 50] → [0, 0.004, 0]`. The two segments are not connected in the file. Independent recomputation: each segment is about 111.19 metres horizontally, for a total of about 222.38 metres, rounded to 222 m; segment A is +50 m and segment B is −50 m; minimum 0 m, maximum 50 m; grade on each pair is 50 ÷ 111.19 × 100% ≈ 45.0%; the profile keeps 4 points. The common mistake is to connect the end of A to the start of B, adding an extra horizontal distance and a flat 50-metre connector. The tool does not join segments, so the gap between them is not counted in total distance.

### Case matrix

Existing cases side by side by input, expected output and coverage. Values come from `data/cases`; nothing is re-derived by hand.

| Case | Input | Expected | Coverage |
|---|---|---|---|
| `case-route-elevation-hill` | `{"track":{"format":"gpx","segments":[[{"lon":0,"lat":0,"elevation":0},{"lon":0,…` | `{"gainMeters":100,"lossMeters":100,"minElevationMeters":0,"maxElevationMeters":…` | Typical |
| `case-route-elevation-missing` | `{"track":{"format":"gpx","segments":[[{"lon":0,"lat":0,"elevation":null},{"lon"…` | `{"gainMeters":null,"lossMeters":null,"profilePoints":0,"warning":"elevation-mis…` | Second unit/boundary |
| `case-route-elevation-segments` | `{"segments":[[[0,0,0],[0,0.001,50]],[[0,0.003,50],[0,0.004,0]]]}` | `{"distanceMeters":222,"gainMeters":50,"lossMeters":50,"minElevationMeters":0,"m…` | Third unit |

## Reading the result

Read total distance and the scale of climbing first, then look for steep rises, steep drops and long climbs in the profile, alongside aid points, surface and weather. "Unknown" elevation means the data is missing, not that the route is flat. Maximum grade describes one adjacent pair; it does not give the average difficulty of a climb or replace judgments about technical terrain, traffic or rockfall. The elevation range can help you decide clothing and fuel, but it does not assess air density, visibility or surface slipperiness.

## Rounding and tolerance

Distance, ascent and descent round to the nearest whole metre with a ±0.5 m tolerance. Elevation keeps one decimal with ±0.05 m; grade keeps one decimal with ±0.05 percentage points; profile points use whole-metre distance and two-decimal elevation. GPS elevation drifts, and devices, barometers and correction methods produce different totals, so displayed precision is not real accuracy. Compare routes from the same source and elevation basis where possible. When recomputing by hand, keep intermediate values rather than dividing rounded figures again.

## Common pitfalls

The first pitfall is treating maximum grade as the average difficulty of the whole route: it comes from one adjacent pair, and the average grade of a long gentle climb can be far lower. The second pitfall is using a simplified track as if it were the raw record: track compression deletes points and their elevation, which usually lowers the gain. The third is comparing gain across devices without checking recording method: the same route recorded by a barometric watch, a phone and another watch can produce materially different totals. The fourth is reading unknown elevation as zero metres or flat ground, which discards the up-and-down information outright.

## Limits and when not to use it

Elevation is used as recorded and GPS elevation is noisy. Segments are measured independently and endpoints are not joined. Grade is a point-pair estimate, not a smoothed road-design grade. Files are read locally. The tool does not certify the course or assess surface, technicality or safety. It is not suitable for deciding whether a course is official, permitted or race-ready, or for inferring finish time from maximum grade. When you need certified gain, route permission, or judgments about rockfall, visibility or traffic, use the event handbook, on-site reconnaissance and official maps.

## How to use it

1. Export a GPX or GeoJSON with elevation from the watch or app, and confirm it is line geometry with elevation fields.
2. Open it locally and read distance, ascent, descent, elevation range and maximum grade, then inspect the profile for key steep sections.
3. If elevation is missing or partial, repair the source or use official elevation data; when comparing routes, keep one source and basis.

## Related reading

- [Uphill and downhill running: pace, form and cost](/en/knowledge/uphill-and-downhill/)
- [Trail navigation: tracks, maps and backups](/en/knowledge/trail-navigation/)
- [Route safety and shared-path etiquette](/en/knowledge/route-safety/)
- [Track view: reading an activity on the map](/en/tools/track-view/)
- [Track simplification: fewer points and elevation loss](/en/tools/track-simplify/)

## Privacy and data

The file is parsed locally and not uploaded; results are not saved after the page closes. Oversized or malformed files produce an error rather than a partial result. Check whether the start reveals a home address or frequent location before sharing; avoid publishing raw coordinates directly.

## Sources and scope

File boundaries follow the public GPX and GeoJSON specifications; distance and geodesy follow WGS84; uphill and downhill mechanics follow sports-biomechanics reviews. Elevation comes from the file itself. The tool makes no guarantee about device accuracy, route safety or course certification. Where a parameter lacks a traceable basis, the text labels it as an estimate rather than inventing a precise constant. Verified 2026-11-26.

<!-- related-ring -->
## Related entries

- [Track conversion: convert GPX and GeoJSON lines](/en/tools/track-convert/)
- [Track simplification: projected tolerance, points and distance](/en/tools/track-simplify/)
- [Track viewer: read your GPX and GeoJSON locally](/en/tools/track-view/)
