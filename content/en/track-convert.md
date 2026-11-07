---
entityId: tool:track-convert
locale: en
title: "Track conversion: convert GPX and GeoJSON lines"
summary: "Convert a GPX or GeoJSON line to the other format locally, keeping coordinate order and existing elevation while stripping timestamps, device names, personal names and original metadata."
aliases: ["track conversion", "GPX to GeoJSON", "format conversion"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

Track conversion reads one line, re-serializes it in the format you choose and offers a download. It is for users who need a watch or app GPX turned into GeoJSON for a mapping tool, or a GeoJSON line turned into GPX for other software. It changes file structure, not geometry. It does not decide whether the line is an official course, permitted or suitable for a race, and it does not certify distance or elevation. For statistics use the track viewer; to reduce points use the simplifier.

## Conversion rules and accepted inputs

The core is a reversible serialization rule: read coordinates in their original order and write them in the target format without inserting, deleting or reprojecting points.

| Input | Accepted objects | Output | Preserved |
| --- | --- | --- | --- |
| GPX | `trkseg` under `trk`; `rte` when no trkseg exists | GPX or GeoJSON | Order, segments, existing elevation |
| GeoJSON | `LineString`, `MultiLineString`, and `Feature`/`FeatureCollection` containing only those | GPX or GeoJSON | Longitude, latitude, optional third elevation |
| Other geometry | Points, polygons and similar | Rejected | No silent discard; an error is returned |
| Metadata | Timestamps, device, names, file name | Not written | Actively stripped |

- Each `trkseg` or `rte` is a separate segment; endpoints of different segments are not joined.
- Missing elevation stays missing; it is never written as zero or a placeholder.
- The output is re-serialized, so indentation, number formatting or element order can differ even at the same format.
- Files are limited to 20 MB and 200,000 coordinates; processing is local.

## Worked example

Assume a GeoJSON line with three positions: `[0, 0, 10]`, `[0.001, 0]`, `[0.002, 0, 15]`.

| Check | Expected | Meaning |
| --- | --- | --- |
| Segment count | 1 | One LineString |
| Coordinate count | 3 | Conversion adds and removes nothing |
| Positions with elevation | 2 | First has 10, last has 15 |
| Middle elevation | Missing | Must not become zero |

After conversion the file should still have one segment and three coordinates, two of them with elevation. Order and values must not change. An independent round-trip check produces these values, not the page display.

## Rounding and tolerance

Coordinates and elevation are preserved as parsed, with no rounding or truncation, so the numerical tolerance is zero. File size is reported in bytes for display only. No coordinate transformation is applied, and the WGS84 longitude-first order is retained.

## Reading the result

A successful conversion is judged by matching point count, segment count and elevation coverage, not by the file “looking similar”. Fewer points usually means the input geometry was misread or rejected; fewer elevation values means elevation was lost during parsing. Conversion cannot prove the line is correct, complete or authorised, and it cannot turn a track into an official course file.

## How to use it

1. Export GPX or GeoJSON from the source device or app and confirm it is line geometry.
2. Choose the target format and convert, noting point count, segment count and elevation coverage.
3. Reopen the output with the track viewer and compare endpoints, points and distance before sharing.

## Limits and when not to use it

Coordinates must be WGS84 longitude and latitude in that order. Only line geometry is accepted; other geometry types are rejected rather than silently dropped. Distance, when read elsewhere, is the WGS84 distance between consecutive points and informational only. Conversion is re-serialization, not a byte-for-byte copy. Missing elevation is not invented, and files over 20 MB or 200,000 points are rejected before parsing. It is not suitable when timestamps, heart rate, cadence or other extension fields must be preserved, or when a track is expected to prove permission or certification.

## When this number misleads you

It assumes WGS84 longitude and latitude in that order and accepts line geometry only. If the file is actually in an obfuscated datum such as GCJ-02, the whole geometry shifts: the distance can look normal while the position is wrong. Conversion re-serialises the file, so timestamps, heart rate and cadence extensions are not preserved; distance is a geodesic sum between consecutive points, informational only and not a certified course length.

Do not use it for course measurement, permit decisions or preserving track evidence, and do not assume that a convertible file is licensed for redistribution.

## Related reading

- [Trail navigation: tracks, maps and backups](https://learn.paobu.org/en/articles/trail-navigation/)
- [Route safety: plan, weather and escape route](https://learn.paobu.org/en/articles/route-safety/)

## Privacy and data

The download is generated locally in the browser. Contents are not uploaded, logged or retained after a refresh, and the original file is never modified or overwritten. On a shared computer, think twice before opening a track that reveals a home address; remove private locations near the start before sharing.

## Sources and scope

File structure follows the GPX 1.1 specification and RFC 7946 GeoJSON; coordinate order and elevation fields follow those public definitions. The tool changes format only and does not certify the line. Verified 2026-11-06.
