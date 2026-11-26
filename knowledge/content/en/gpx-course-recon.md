---
entityId: knowledge:gpx-course-recon
locale: en
title: "GPX and course recon: turn a track into an executable checkpoint table"
summary: "GPX is not a navigation guarantee. This page covers trk/rte/wpt, six steps after download, profile and climb conventions, checkpoint/cut-off alignment, offline backups, licence boundaries and a ground-recon checklist."
aliases: ["GPX", "赛道侦察", "course recon", "轨迹", "track"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this page solves

GPX is not a “download and go” navigation file. It may be a track, a set of route points, a checkpoint collection, or a simplified line. Without version, datum, licence and ground-truthing, a GPX can take you further into the wrong place.

This page follows the minimum course-recon sequence: get the file, read the profile, mark checkpoints, make offline backups, and check on the ground. It does not host any race track; obtain one from the official entry and check its licence.

## What GPX is and is not

GPX is an XML exchange format with `trk` (track), `rte` (route) and `wpt` (waypoint) elements. A track is a recorded point sequence, a route is a planned sequence, and a waypoint is an isolated point; they are not interchangeable.

GPX is not an official map, a closure notice or a rescue guarantee. An official GPX may cover only the main line, without temporary changes, aid stations or escape points; on race day, marshals and markings win.

## Six steps after download

Step one: record the source URL, download date, file size and hash. Step two: open it on both computer and phone. Step three: check whether it has `trk` and `wpt`. Step four: overlay it once on the official map. Step five: mark start, finish, checkpoints, cut-offs and escape points. Step six: export an offline map.

Keep a record at every step: name the file with race, year, version and date, for example `race-2026-v2-2026-11-26.gpx`. A GPX without a version is not a race-day tool.

## How to read the profile

Read total distance, cumulative climb and high/low points first, then climb density per 5 km. The same 1,000 m of climb concentrated in 10 km and spread over 50 km has completely different pacing and fuelling consequences.

The smoothing window changes the number: a 10 m threshold, a 5 m threshold and raw GPS elevation give different cumulative climbs. Record the threshold you used; never compare two climbs computed with different methods.

## Checkpoints and cut-offs

Copy the official checkpoint table into three columns: name, kilometre/climb, cut-off. Then calculate latest arrival and target arrival, leaving a 30–45 minute margin.

GPX waypoints may not contain cut-off times; the race guide is the cut-off authority. Match the GPX checkpoints against the guide; if one is missing, the guide wins. Do not substitute a track point for a checkpoint.

## Offline and backup

Carry at least two offline copies on race day: phone offline map plus watch track, with a paper checkpoint/cut-off card as the third. A phone in airplane mode can still show an offline map; when the watch dies, the paper card still lets you judge position by kilometre.

Do not keep the GPX only in the cloud. With no signal, the cloud does not open. Before the start, keep one copy on phone, one on watch and one on paper, plus a power bank or spare batteries.

## Licence and redistribution

“Publicly visible” does not mean “redistributable”. An official GPX may have no licence statement, or may allow personal use only. Uploading it to a public site, bundling it in an app or reselling it can infringe rights.

This page records the official entry and licence status; it does not host GPX. For reuse, find an explicit licence; if none, link to the official entry and do not republish the file.

## Ground recce

A ground recce does only four things: confirm start/finish access, confirm checkpoint locations, confirm escape routes and confirm hazards (cliffs, river crossings, road crossings, construction). Do not walk the whole course under the name of recon; save the legs for race day.

If you cannot visit, do a desktop recce with the official map and satellite imagery, and mark uncertainties red. On race day, slow down at red points and check markings rather than memory.

## Common mistakes

Mistake one: using someone’s Strava track as the official course. Two: reading total climb but not its distribution. Three: trusting GPX when it disagrees with the guide on checkpoints. Four: storing only in the cloud. Five: forwarding the track to a public group.

Six: comparing raw GPS elevation with smoothed climb. Seven: opening the file for the first time on race day. Each turns “having a GPX” into “being more exposed”.

## Chinese runner’s perspective

Chinese races often distribute tracks through WeChat or mini-programs, where files may be compressed, renamed or replaced by screenshots. First confirm GPX versus KML, then the datum; a screenshot cannot navigate.

Mountain signal is uneven, so download offline maps in advance. If the race only publishes an official map, do not substitute a stranger’s track. Use “official entry + offline copy + paper card” as the standard kit.

## Checklist

File: source, date, version, hash, complete trk/wpt. Map: official overlay, checkpoints/cut-offs, escape points, hazards. Devices: phone offline, watch track, power bank, paper card. Licence: redistribution allowed?

Open it once 48 hours before the start; on race morning, only verify, do not re-download.

## Related reading and tools

Read [trail navigation](/en/knowledge/trail-navigation/) for map and bearing basics; use [track view](/en/tools/track-view/) to check start/finish and profile, and [track simplify](/en/tools/track-simplify/) to control file size.

Route pages state `geometryAccess`; when it is not redistributable, they link to the official entry instead of hosting a local file.

## 来源与核验边界

本页的 GPX 机制与官方文件事实来自赛事官网与公开格式说明；每条来源的 claims 与 claimVerification 见实体 JSON。本页不托管任何赛事轨迹，不提供导航文件。

最后核验：2026-11-26。下一次复核触发：官方 GPX 更新、许可变化、格式/坐标系说明变化。## Race-day sequence

Thirty minutes before the start: open the offline map and confirm your position and the start. Ten minutes before: put the paper card in the bib pocket and set the watch to the navigation page. After the gun: at every checkpoint, check the number first, then the cut-off; do not rely on “about right”.

If the track drifts, stop and check contours and landmarks; do not follow the drift. GPX is an aid; when markings, marshals and other runners agree, the ground wins.


