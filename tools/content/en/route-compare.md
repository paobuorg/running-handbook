---
entityId: tool:route-compare
locale: en
title: "Course comparison: compare published versions field by field"
summary: "Select 2 to 4 published course versions and compare distance, elevation, surface and technicality. Missing values stay unknown, and no safety or difficulty ranking is produced."
aliases: ["course comparison", "route compare", "elevation compare"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this tool answers

Course comparison places 2 to 4 **published** course versions in one table and shows distance and its recording basis, elevation gain and its basis when recorded, surface type when recorded, and technicality when recorded. It is for runners choosing a race and checking official fields side by side, and for editors checking that published versions of one event are consistent. It does not rank courses or read a longer distance, more climbing or a technicality value as “harder” or “more dangerous”. Suitability depends on training, weather, aid, access rules and condition on the day; a field table cannot derive it. For a safety assessment or a difficulty score, this tool is not suitable.

## Decision rules and field handling

- Only 2 to 4 distinct published versions can be selected; fewer, more or duplicate identifiers return an error.
- Each row is a field and each column a version; column order follows selection order.
- Missing elevation, surface or technicality stays unknown; it is never filled with zero or inferred from another version.
- The table records fields only: no total score, ranking, difficulty index or safety grade.

| Field | Recorded content | When missing |
| --- | --- | --- |
| Distance | Metres recorded for the course | Null, shown as unknown |
| Elevation | Gain plus its basis | Null, shown as unknown |
| Surface | Surface type from an official or source record | Null, shown as unknown |
| Technicality | Technical description from the source | Null, shown as unknown |

Each version keeps its basis notes, so figures from different sources are not presented as one ruler.

## Worked example

Assume two synthetic versions: alpha is 42,195 m with 300 m gain, road surface and no technicality; beta is 21,097.5 m with no elevation, surface or technicality.

| Field | alpha | beta |
| --- | --- | --- |
| Distance | 42,195 m | 21,097.5 m |
| Elevation | 300 m | Unknown |
| Surface | road | Unknown |
| Technicality | Unknown | Unknown |

Both columns keep their values, beta's three gaps show as unknown, and no ranking field appears.

## Rounding and tolerance

Distance is shown in kilometres to three decimals with a ±0.0005 km tolerance; elevation is shown in whole metres with ±0.5 m. Missing values stay unknown, are not rounded and never become zero. Surface and technicality are text fields, kept with leading and trailing whitespace removed; no normalisation or synonym merging is applied. Values may come from different measurement methods and are not converted to one standard.

## Reading the result

The table helps you see differences, not draw conclusions. A longer course is not automatically harder, and more climbing does not automatically mean slower. Surface and technicality are descriptions too. A column with many gaps has incomplete verification and cannot be read as “easier”. Whether a track geometry is public and redistributable is separate from whether fields can be compared; a visible course page does not grant redistribution rights. After comparing the two columns, return to each course page to check the source year and recording method, so figures from different versions are not treated as one measurement.

## How to use it

1. Pick 2 to 4 published versions and confirm their identifiers are distinct.
2. Read each field, and when you see “unknown”, check the course's source notes instead of filling a value yourself.
3. Treat the table as one input alongside training, weather, aid and access information; do not turn it into a ranking.

## How to read missing fields

| Table state | Meaning | How to handle it |
| --- | --- | --- |
| Distance, elevation, surface and technicality all recorded | Fields can be compared side by side | Check each column's recording basis first |
| Elevation missing | Gain was not verified for that version | Unknown; do not infer from another version |
| Surface or technicality missing | The source did not record the field | Unknown; do not judge by distance alone |
| A column has many gaps | That version's verification is incomplete | Do not read it as "easier" or "gentler" |

Read the basis notes first: one course measured officially and another by GPS can differ by hundreds of metres of gain that reflect method, not difficulty. The table does not convert figures from different sources to one standard, and surface or technicality text is not synonym-merged; wording differences such as road, paved and asphalt are kept as written.

A longer distance or more climbing does not automatically mean harder or slower; difficulty also depends on altitude, weather, surface, aid and condition on the day. The table lists recorded fields only, as one input to race choice, and produces no safety grade, difficulty index or recommendation ranking.

## Limits and when not to use it

Only published versions can be compared; drafts and work in progress are not verified records. Distance and elevation may come from different official sources and methods, and the table shows the basis rather than pretending to one standard. Missing means unknown, not zero. Geometry availability and licensing vary by course and are not granted by visible fields. The tool produces no safety, difficulty or suitability ranking and is not suitable for course certification, access decisions or live condition checks.

## When this number misleads you

Only published routes are eligible, and distance and elevation may come from different official sources and measurement methods: one certified course and one GPS trace can differ by hundreds of metres of gain that reflect method, not difficulty. A missing value means unknown, not zero; the tool never fills gaps, so a complete-looking table is not necessarily complete data. Ranking by distance plus gain ignores surface, technicality, altitude and weather.

Do not use it for course certification, permit decisions or live conditions, and do not turn it into a safety, difficulty or suitability ranking. Visible geometry does not grant redistribution rights.

## Related reading

- [Records and course validity: when a length counts](/en/knowledge/records-and-course-validity/)
- [Uphill and downhill running: pace, form and cost](/en/knowledge/uphill-and-downhill/)
- [Track viewer: read your GPX and GeoJSON locally](/en/tools/track-view/)

## Privacy and data

All comparisons happen locally; no account is required. Inputs are written into the page URL query string so they survive a refresh and can be shared. Opening that URL sends it to the static host and leaves it in browser history. Clear the address-bar parameters after using a shared device.

## Sources and scope

The standard marathon distance follows World Athletics; the Boston Marathon and UTMB example fields come from their official pages. The tool displays recorded fields only and does not certify distance or judge safety. Verified 2026-11-06.

<!-- related-ring -->
## Related entries

- [Route elevation: a local GPX elevation profile](/en/tools/route-elevation/)
- [Track conversion: convert GPX and GeoJSON lines](/en/tools/track-convert/)
- [Track simplification: projected tolerance, points and distance](/en/tools/track-simplify/)
