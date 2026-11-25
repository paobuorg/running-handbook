# 贡献说明

本仓库接收跑步知识正文、工具说明、公式契约、来源、审阅与算例。网站代码、交互实现和设计资源分别在 `site-www`、`site-knowledge`、`site-tools` 与 `paobu-core`。

## 提交前

1. 确认 `entityId` 与 `slug` 唯一；知识内容只属于一个主主题，工具内容写清解决的唯一问题。
2. 先写读者问题和适用条件，再给结论、依据、步骤与例外；不要把多个主题拼成没有主线的长文。
3. 为事实、数值、健康建议和因果表述记录 `sourceId`、URL 或 DOI、定位段与支持的结论。研究结论、经验建议和个人推断分开写。
4. 工具必须在 `formulaDescription` 写清输入、运算顺序、单位、边界和舍入；在 `assumptions` 逐条列简化条件；为每个数值规则增加或更新 `data/cases/` 中的独立算例。
5. 修改计算口径必须提升 `specVersion`，并同步 `site-tools` 的实现与测试；不能只改说明或只改代码。
6. 中英文分别成稿，不把机器翻译直接当英文成稿；两种语言的事实、数值与限制条件必须一致。
7. 不编造作者、资质、实测、审阅者或引用。伤病、慢病、孕产等具体干预建议需要相应专业审阅；没有审阅能力时保留为草稿。
8. 图片、图表和引用片段只使用权利明确且允许再分发的材料，按来源要求署名。

## 审阅与状态

状态为 `draft`、`in-review`、`published`、`withdrawn`。新内容从 `draft` 开始，完成双语、来源与许可检查后进入 `in-review`。`published` 需要两种语言都有作者与审阅者，并存在 `approve` 审阅记录；审阅摘要必须与当前正文一致。`reviewedAt` 不能由格式化、翻译或重建自动填写，正文改变后必须重新审阅。

## 校验

在 `site-knowledge` 或 `site-tools` 运行内容校验和构建。校验器会检查双语配对、主题、来源引用、许可、审阅日期、内容摘要、工具契约与算例。失败时修正内容，不绕过检查。

## 来源与礼貌

- 不复制官方页面、论文全文、Logo、GPX 或数据库，除非来源明确允许。
- 不把个人轨迹直接公开；先移除时间、设备、住址和起点附近的敏感位置，并取得授权。
- 纠错请指出具体段落、现有来源与建议来源。没有公开 Issue 地址时，不虚构邮箱或联系人。

---

# Contributing

This repository accepts running knowledge, tool documentation, formula contracts, sources, reviews and test cases. Site code, interactive implementations and design assets live in `site-www`, `site-knowledge`, `site-tools` and `paobu-core`.

Before submitting, check that the `entityId` and slug are unique, state the reader's problem and scope, and locate sources for facts, numbers and causal claims. Tool entries must document inputs, operation order, units, boundaries and rounding, and each numeric rule needs an independent case under `data/cases/`. A calculation change requires a new `specVersion` and a matching change in `site-tools` code and tests.

Write both languages independently. Do not invent authors, qualifications, measurements, reviewers or citations. Specific health, injury or pregnancy guidance needs review by someone with the relevant expertise; otherwise keep it as a draft. Only include images, charts or quotations whose redistribution rights are confirmed and recorded.

New entities start as `draft`, move to `in-review` after bilingual and rights checks, and to `published` only with authors, reviewers and an `approve` review record in both languages. Re-run content validation and the site build after changes. Do not bypass a failed check.
