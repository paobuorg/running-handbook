---
entityId: tool:track-simplify
locale: en
title: "Track simplification: projected tolerance, points and distance"
summary: "Simplify each segment independently with a local metric projection and iterative RDP, keeping endpoints and segment breaks while reporting the change in points and WGS84 distance. The original file is never modified."
aliases: ["track simplification", "RDP", "point reduction"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool does

The simplifier reads a GPX or GeoJSON line, removes points that contribute little to its shape within a chosen tolerance, and produces a new file for download. It reports points before and after, WGS84 distance before and after, and a per-segment comparison. Simplification is **lossy**: removed points and their elevation disappear from the output, and the original file is never modified. If the file is an archive, a course measurement or evidence, do not simplify it.

## Calculation rules and RDP steps

1. For each segment, compute its mean latitude and project longitude and latitude to local metres around that latitude.
2. Run an iterative Ramer–Douglas–Peucker (RDP) pass in the projected plane: keep the first and last points, repeatedly find the point farthest from the current chord, keep it when the distance exceeds the tolerance, and continue on both sides.
3. Output retained points in original order and recompute distance before and after with WGS84 geodesic inverse distances.

| Parameter or check | Value | Meaning |
| --- | --- | --- |
| Tolerance | 1 to 100 metres, default 10 | Maximum allowed point-to-chord deviation in the projected plane |
| Segment span | Projected bounding-box diagonal ≤ 500 km | Larger segments are refused |
| Longitude span | ≤ 180 degrees | Larger spans may cross the antimeridian |
| Latitude | Any point ≤ 85 degrees | Beyond this the segment is refused |
| Output format | Same as input | GPX stays GPX, GeoJSON stays GeoJSON |

The tolerance is **projected metres**, not geodesic distance. Because the projection is local, tolerance and ground distance can differ slightly away from the centre; the page reports the WGS84 distance change separately. RDP limits point-to-chord deviation, not the change in total distance.

## Worked example

Assume three points near the equator: `[0, 0]`, `[0.001, 0.00005]`, `[0.002, 0]`.

| Tolerance | Middle offset | Decision | Points after |
| --- | --- | --- | --- |
| 10 m | About 5.56 m | Below tolerance, removed | 2 |
| 1 m | About 5.56 m | Above tolerance, kept | 3 |

The middle point deviates from the chord by 0.00005 degrees of latitude, about 5.56 metres. At 10 metres it is removed and the endpoints remain; at 1 metre it is kept.

## Rounding and tolerance

The tolerance is used as entered between 1 and 100 metres with no extra rounding. Point counts are integers. Distances before and after are rounded to the nearest whole metre with a ±0.5-metre tolerance. Retained coordinates and elevation are not rounded. Tolerance and distance change are different; a small distance change does not prove an unchanged shape.

## Reading the result

Look first at how many points were removed, then at the distance change. A large point reduction with a small distance change usually means the original was densely sampled. A clear distance change means the tolerance is large relative to the bends; lower it and retry. Per-segment statistics show where compression was strongest, but they do not prove the simplified line is official or safe for navigation.

## How to use it

1. Read the original point count and distance, and confirm the file is within 20 MB and 200,000 points.
2. Enter a tolerance from 1 to 100 metres, starting near the default 10, and record points and distance before and after.
3. If the shape change is unacceptable, lower the tolerance and retry; download the result and keep the original file.

## Common tolerance choices

| Tolerance | Typical use | Point change | Shape risk |
| --- | --- | --- | --- |
| 1–3 m | Twistier routes that need the outline kept | Smaller reduction | Distance and gain stay close to the original |
| 10 m (default) | Map display, general sharing | Moderate reduction | Sharp bends may be smoothed |
| 30–100 m | Rough schematic, zoomed-out map | Large reduction | Local shape changes clearly |
| Two-point segment | Any tolerance | Both endpoints always kept | No middle point to remove |

Look first at the point difference and the distance difference: a large point drop with a small distance change usually means the original was densely sampled; a clear distance change means the tolerance is large relative to the bends, so lower it and retry. Tolerance is the point-to-chord distance in projected metres, not a geodesic distance and not an upper bound on distance change; RDP constrains point-to-chord deviation only and does not preserve every sharp bend's elevation detail.

Removed points and their elevation disappear from the output and cannot be recovered from the simplified file. Keep the original for precise archives, course measurement or evidence; do not replace it with the simplified version. The output keeps the input format, and the downloaded file should still be checked with the viewer for endpoints and distance.

## Limits and when not to use it

Tolerance is measured in the projected plane, not as a geodesic distance. Segments spanning more than 180 degrees of longitude, reaching beyond 85 degrees latitude or with a projected diagonal above 500 km are refused. Only line geometry is accepted, and removed points lose their elevation. The simplified file is a new download and the original is untouched; files over 20 MB or 200,000 points are rejected. It is not suitable for archives, course measurement or evidence that require every sample.

## When this number misleads you

Tolerance is measured in a projected plane, not as geodesic distance; the default 10 m deletes many points on a twisty course, and the simplified distance and gain usually fall, with deleted elevations unrecoverable. A segment is rejected when its longitude span exceeds 180 degrees, any point lies beyond 85 degrees latitude, or its projected bounding box diagonal exceeds 500 km. It accepts line geometry only and cannot decide which points carry evidentiary value.

Do not use it for course measurement, track evidence or archives that must keep every sample, and do not back-calculate the original track from simplified statistics.

## Related reading

- [Trail navigation: tracks, maps and backups](/en/knowledge/trail-navigation/)
- [Uphill and downhill running: pace, form and cost](/en/knowledge/uphill-and-downhill/)
- [Track viewer: read your GPX and GeoJSON locally](/en/tools/track-view/)
- [Track conversion: convert GPX and GeoJSON lines](/en/tools/track-convert/)

## Privacy and data

The file is read and processed only in your browser, not uploaded or retained after a refresh. Check whether the start reveals a home address before sharing; simplification does not remove sensitive locations.

## Sources and scope

The RDP method follows Ramer (1972) and Douglas–Peucker (1973); coordinates and distance follow WGS84 and GeographicLib as used by core; formats follow GPX 1.1 and RFC 7946. It only simplifies geometry and does not certify a course. Verified 2026-11-06.

<!-- related-ring -->
## Related entries

- [Track viewer: read your GPX and GeoJSON locally](/en/tools/track-view/)
- [Acute-to-chronic load ratio: review the last 7 days against 28 days](/en/tools/training-load/)
- [Crew and pacer plan: schedule handoffs against the official access list](/en/tools/crew-pacer-plan/)
