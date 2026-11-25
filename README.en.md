# RUNUP · Running handbook

[中文](README.md) · English

Running knowledge, training methods, health and safety guidance, plus reproducible tool documentation, formulas and test cases. This repository keeps the **content** together while the sites remain separate: knowledge at `learn.paobu.org`, tools at `tools.paobu.org`.

## What is here

- **90 knowledge pieces** across nine topics: training, technique, recovery, nutrition, gear, health, safety, habits and culture, including concepts, guides, checklists, learning paths and a glossary.
- **18 running tools**: pace, splits, run-walk, race prediction, fueling, carb loading, heat adjustment, training load, injury-risk check, shoe mileage, race checklist, track view/convert/simplify, elevation analysis, grade-adjusted pace, sweat rate and route comparison.
- **216 bilingual detail pages**, 247 sources and 43 independent test cases.
- Knowledge articles and tool contracts share one source, review and digest model; formulas, assumptions, rounding and boundary cases are all checkable.

## Why one repository

Knowledge and tools answer the same kind of question: “How should I run this, fuel this, or judge this session or course?” Keeping them together lets a reader move from an article to the matching tool, and lets contributors maintain both under one evidence standard. The tools site stays separate because calculators and file handling need their own deployment.

## Layout

```text
knowledge/
  content/zh-CN/{slug}.md            Chinese knowledge article
  content/en/{slug}.md               English knowledge article
  data/entities/{slug}.json          Topic, type and source refs
  data/sources/{sourceId}.json       Sources and supported claims
  data/reviews/{slug}.{locale}.json  Review record and digest
tools/
  content/zh-CN/{slug}.md            Chinese tool documentation
  content/en/{slug}.md               English tool documentation
  data/entities/{slug}.json          I/O contract, formula, assumptions, rounding
  data/cases/{caseId}.json           Independent test case
  data/sources/{sourceId}.json       Standards, papers and public guidance
  data/reviews/{slug}.{locale}.json  Review record and digest
```

Each subtree keeps its own complete `content/`, `data/` and `assets/` structure; site builds read them as separate knowledge and tool roots.

## Content rules

- Each entity has one primary topic; secondary topics, audiences and settings live in separate fields.
- Numbers, effects and causal claims need a locatable source; research findings, practical advice and inference are kept distinct.
- Specific health, injury or pregnancy guidance needs review by someone with the relevant expertise; otherwise it stays a draft.
- Tools must state inputs, operation order, units, boundaries and rounding; changing the calculation requires a new `specVersion` and matching cases.
- Chinese and English must agree on facts, limits and error conditions; machine translation is not an English final draft.

## Review status

All 108 entities have completed AI-assisted editorial review and are published (`published`, with bilingual `approve` records and matching digests). The reviewer is `runmap-editorial`, explicitly AI-assisted, not independent or professional medical/nutrition review. This repository does not claim professional review.

## Local use

The content is read by `site-knowledge` and `site-tools` at build time. When the six projects sit in the same parent directory, the defaults point to `running-handbook/knowledge` and `running-handbook/tools`; `KNOWLEDGE_CONTENT_DIR` and `TOOLS_CONTENT_DIR` can override them.

This repository has no install or build command. Content validation, site builds and search indexing happen in the site repositories.

## Licence and corrections

- New articles, tool documentation and cases: CC BY 4.0, attributed to “RunUp 跑起来”.
- Third-party sources, quotations, images and linked material: under each source's terms, recorded per entity or source.
- Site code: MIT, in the three `site-*` repositories and `paobu-core`.

Report factual, formula or source problems through an issue or pull request that names the paragraph, source and proposed change. See [CONTRIBUTING.md](CONTRIBUTING.md).

Last checked: 2026-11-25.
