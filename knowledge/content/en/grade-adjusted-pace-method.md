---
entityId: knowledge:grade-adjusted-pace-method
locale: en
title: "Grade-adjusted pace (GAP): compare effort across climbs"
summary: "GAP does not turn a trail race into a road time. This page covers grade cost, inputs, downhill limits, road/trail differences, race segments and a review table."
aliases: ["GAP", "坡度配速", "grade adjusted pace", "爬升折算", "坡度换算"]
authors:
  - runmap-editorial
reviewers:
  - runmap-editorial
translationStatus: reviewed
---

## What this page solves

Grade-adjusted pace (GAP) answers one question: what flat-equivalent pace does this climb or descent represent? It is used to compare effort across routes, set race segments and check whether you started too fast, not to turn a trail race into a road time.

This page covers the boundaries, required inputs, why downhill cannot be discounted forever, and how to cross-check GAP with heart rate and feel. It does not offer a single formula or claim that one tool’s number is the truth.

## Why grade changes pace

Uphill adds gravitational work; at the same pace, cardiorespiratory and leg load rise. Downhill is not free speed: eccentric contraction, braking and attention raise the cost. The steeper the grade, the less linear the cost per kilometre.

So “5:00/km on the flat stays 5:00 on a 10% climb” is false. GAP makes the difference comparable; it does not ask you to chase flat pace uphill.

## Core assumptions of GAP

GAP assumes an estimable extra metabolic cost for a given grade and speed, then converts that cost into a flat-equivalent pace. Models differ in how they handle walking, steep grades and technical terrain, so different tools produce different numbers.

It does not assume you can hold that equivalent pace, nor that downhill keeps giving free speed. GAP is cost conversion, not performance prediction; treat it as a prediction and you will blow up in the second half.

## What inputs you need

Minimum inputs: distance, climb/descent and time per kilometre or segment. For better accuracy: segment grade (not race average), surface (road, dirt, gravel, technical rock), altitude and weather.

A race-average grade flattens “short steep climb plus long gentle descent”. Use segments, at least per checkpoint or 5 km; mark technical terrain separately and do not let GAP replace technical difficulty.

## Why downhill is not unlimited

Downhill GAP benefit is clearest on gentle grades; steeper descents are offset by eccentric damage, braking, foot placement and attention. A very steep descent may produce a fast “equivalent pace”, but your quadriceps and ankles do not pay at that rate.

Use downhill GAP to ask “what is this section roughly worth on the flat”, not “how fast can I bomb this descent”. Technical descents are governed by RPE and segment time, not GAP ranking.

## How to use the tool

Load the GPX or segment table into the [grade-adjusted pace tool](/en/tools/grade-adjusted-pace/) and choose a consistent model. Copy the output into three blocks: early, middle, late. Set a GAP range per block, not a second-by-second target.

Cross-check with heart rate and feel: if GAP says “this is 4:50 on the flat” but heart rate is already threshold, slow down. GAP is planning language, not a race-day command.

## Road versus trail

Road grades are usually short and surfaces consistent, so GAP is more useful for pace planning. Trail grades are long, surfaces complex and descents technical; GAP explains only part of the cost. Treating a trail GAP as road pace underestimates ankles, hips and attention.

Plan trail by segment effort and checkpoint time, not by a race-wide GAP. GAP can compare climb cost between routes; it cannot replace technical training.

## How to set race segments

Cut the course into 5–8 checkpoint segments. For each: distance, climb, descent, surface, target time and latest arrival. GAP estimates the flat-equivalent pace; target time still adjusts for technical difficulty and aid stations.

The first 20% should be conservative; the middle follows the plan; the last 30% follows feel and checkpoint margin. Do not make negative splits a hard rule; trail negative splits are often broken by descents and night.

## Common mistakes

Mistake one: using race-average grade. Two: treating downhill GAP as free speed. Three: comparing different models. Four: using GAP instead of technical training. Five: race-day second-by-second GAP targets.

Six: ignoring altitude and weather. Seven: treating GAP as performance prediction. Each turns “scientific pacing” into “paper pacing”.

## Chinese runner’s perspective

Chinese trail profiles often use different smoothing. Confirm the source of the climb number before feeding GAP. Do not mix a race WeChat “cumulative climb” with raw GPX elevation.

Chinese road bridges and tunnels cause GPS drift; correct segments with barometric altitude or the official profile. When unsure, use checkpoint time and feel rather than forcing GAP.

## Checklist

Inputs: segment distance/climb/descent/surface/altitude/weather. Model: one fixed version. Output: GAP range and target time per segment. Cross-check: heart rate, RPE, checkpoint margin. Review: compare actual segment time with the GAP estimate.

If any input is missing, label GAP “reference”, not “target”.

## Related reading and tools

Use the [grade-adjusted pace tool](/en/tools/grade-adjusted-pace/) for segments; read [training pace zones](/en/knowledge/training-pace-zones/) for system differences and [uphill and downhill](/en/knowledge/uphill-and-downhill/) for technical descent cost.

Route profiles can feed segments, but do not treat a schematic as official geometry.

## 来源与核验边界

本页的坡度成本与训练强度原则来自公开研究/指南；每条来源的 claims 与 claimVerification 见实体 JSON。GAP 的具体公式因模型而异，本页不宣称唯一算法。

最后核验：2026-11-26。下一次复核触发：模型更新、官方剖面口径变化、工具公式变更。## Interface with technical terrain

GAP converts grade, not technical difficulty. Gravel, roots, wet steps, river crossings and night all make the same GAP take longer. Mark technical sections separately or use checkpoint time; do not hide them inside the formula.

Label each segment runnable, run-hike or hike, then attach a GAP reference. Manage technical sections by passage time, not equivalent pace, so a pretty number cannot lure you into dangerous ground.

## A three-block race example

Early: GAP 10–15 seconds slower than flat target, heart rate capped. Middle: adjust by checkpoint margin; GAP only checks whether you are too fast. Late: feel and latest arrival lead; GAP becomes reference.

If middle GAP is on target but heart rate stays high, slow down. If GAP is slow but checkpoint margin is healthy, do not sprint. The race goal is to reach the finish on plan, not to make GAP look good.


