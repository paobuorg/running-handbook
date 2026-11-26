---
entityId: tool:track-view
locale: en
title: "Track viewer: read your GPX and GeoJSON locally"
summary: "Inspect point count, endpoints, distance and existing elevation for a track in your browser without uploading the file. Missing elevation is shown as unknown, never filled with zero."
aliases: ["track viewer", "GPX viewer", "elevation check"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

The viewer reads a GPX or GeoJSON file you choose, parses and totals it locally, and shows the number of coordinates, the WGS84 geodesic distance along the ordered points, the start and end coordinates, and elevation gain when the file contains elevation. It is for runners checking an activity export, confirming that a file is complete, or getting a rough length. It does not judge pace, compare a track with an official course, or certify the track. If you need to simplify points, convert formats or analyse grades, use the dedicated tools.

## Calculation rules and file handling

| Measure | Rule | When elevation is missing |
| --- | --- | --- |
| Point count | Sum of coordinates in all segments | Unaffected |
| Distance | Sum of WGS84 geodesic distances between consecutive points per segment | Unaffected |
| Start and end | First point of the first segment, last point of the last segment | Unaffected |
| Elevation gain | Sum of positive elevation differences | Unknown, never zero |
| Segments | Each trkseg/rte or LineString is measured separately; endpoints are not joined | Unaffected |

- **GPX 1.1**: read track points (trkpt); fall back to route points (rtept) when no trkseg exists.
- **GeoJSON**: read LineString coordinates in longitude, latitude order, with optional elevation.
- Points and polygons are not treated as a route; files are limited to 20 MB and 200,000 coordinates.
- Distance is an ellipsoidal geodesic sum, not a flat Pythagorean approximation, and no smoothing or correction is applied.

## Worked example

- Three points along the equator from longitude 0 to 0.02, no elevation: about 2,226.39 metres, displayed 2,226 m; point count 3; elevation gain unknown.
- Three points from longitude 0 to 0.002 with elevations 10, 20 and 15 metres: about 222.64 metres, displayed 223 m; positive gain 10 m.
- A file with two separate segments: each segment is summed independently; a nearby end and next start are not joined into extra distance.

These values follow independent WGS84 arithmetic and can be repeated with a geodesic calculator.

## Rounding and tolerance

Distance and elevation gain are rounded to the nearest whole metre with a ±0.5-metre tolerance. Point and segment counts are integers with no tolerance. Coordinates keep the precision stored in the file. Whole-metre display does not mean one-metre measurement accuracy: GPS noise, tunnels and signal loss can exceed it, and jumps are not corrected.

## Reading the result

The tool answers how many points a file has, where it starts and ends, roughly how long it is, and how much climbing it contains when elevation exists. It cannot answer the certified course distance, race-day access, surface safety or whether your pace was sensible. “Unknown” elevation means the file has no usable elevation, not a flat route. When only some points carry elevation, the tool warns instead of filling zeros, because that would undercount gain. Distance in a multi-segment file is summed per segment, and gaps between segments are not joined; a track assembled from several fragments therefore totals less than an algorithm that connects endpoints directly. If the file was recorded in segments, check whether each fragment belongs to the same session before reading it.

## How to use it

1. Export GPX or GeoJSON from the watch or app and confirm it is line geometry, not points or polygons.
2. Open the file locally and read point count, distance, endpoints and elevation gain; check the point count against the original export.
3. If elevation is unknown, check whether the device recorded altitude; if you need grades or a profile, use the elevation analysis tool.

## Common file and coordinate cases

| File source | Typical geometry | Statistics the tool gives | Conclusions it cannot give |
| --- | --- | --- | --- |
| Watch GPX export | One or more trkseg | Points, distance, endpoints, gain | Certified course distance |
| App GeoJSON export | LineString / MultiLineString | Points, distance, endpoints, gain | Whether the race day is open |
| No elevation recorded | Any route | Distance, points, endpoints | Cannot be read as flat |
| Elevation on some points only | Any route | Distance, points, partial-coverage warning | Zero-filled gain |

Check the point count first: if it is clearly below the export record, the file may be truncated or only one segment exported. Distance is the sum of WGS84 geodesic distances between consecutive points; GPS jumps in urban canyons, forest and multipath settings make the distance too long or too short, and the tool does not smooth or correct them. Endpoint coordinates help verify where the route starts and ends, but do not prove the route was verified.

Treat elevation in three states: when every point carries elevation, gain is reported; when none does, gain is unknown; when only some do, a partial-coverage warning is issued. Unknown is not zero, and partial coverage cannot be extrapolated. If your device recorded altitude but the file shows unknown, check the original export for an elevation field.

## Limits and when not to use it

Coordinates are understood as WGS84 longitude and latitude. Only GPX tracks/routes and GeoJSON LineStrings are supported. The file stays in the browser and is not uploaded. GPS noise and gaps are not corrected, and distance is informational rather than a certified measurement. Files above 20 MB or 200,000 points are rejected. The tool is not suitable for deciding whether a course is official, permitted or safe, or for treating a track as proof of a race result.

## When this number misleads you

Coordinates are read as WGS84, and only GPX tracks/routes and GeoJSON LineStrings are supported; separate segments are never joined, so a multi-segment file understates total distance. GPS noise and gaps are not corrected, and in urban canyons, forest or multipath settings the distance error accumulates; elevation noise also makes gain jump. Files over 20 MB or 200,000 points are rejected.

Do not use it to decide whether a course is official, permitted or safe, and do not treat a track as evidence of a result or a finish.

## Related reading

- [Trail navigation: tracks, maps and backups](/en/knowledge/trail-navigation/)
- [Route safety: plan, weather and escape route](/en/knowledge/route-safety/)
- [Track conversion: convert GPX and GeoJSON lines](/en/tools/track-convert/)
- [Track simplification: projected tolerance, points and distance](/en/tools/track-simplify/)

## Privacy and data

The file is read only in your browser, not uploaded to this site's server and not written to server logs. File contents are not retained after a refresh. Do not open files that reveal a home address on a shared computer; remove private locations near the start before sharing a track.

## Sources and scope

File formats follow the GPX 1.1 specification and RFC 7946 GeoJSON; distance handling follows the WGS84 ellipsoid. The tool only totals locally and does not certify a route or guarantee device accuracy. Verified 2026-11-06.

<!-- related-ring -->
## Related entries

- [Acute-to-chronic load ratio: review the last 7 days against 28 days](/en/tools/training-load/)
- [Crew and pacer plan: schedule handoffs against the official access list](/en/tools/crew-pacer-plan/)
- [Cutoff buffer planner: check each checkpoint against the official cutoff table](/en/tools/cutoff-planner/)
