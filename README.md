# 跑起来 · 跑步手册

[English](README.en.md) · 中文

跑步知识、训练方法、健康与安全指南，以及可复现的跑步工具说明、公式和算例。这个仓库把**内容**放在一起，网站仍分开部署：知识在 `learn.paobu.org`，工具在 `tools.paobu.org`。

## 这里有什么

- **90 篇知识内容**，覆盖训练、技术、恢复、营养、装备、健康、安全、习惯、文化九个主题，含概念、指南、清单、学习路径和术语表。
- **18 个跑步工具**：配速、分段、跑走结合、比赛预测、补给计划、碳水加载、热适应、训练负荷、伤病风险自检、鞋里程、比赛清单、轨迹查看/转换/简化、高程分析、坡度配速、出汗率、路线参数比较。
- **216 个双语详情页**、247 个来源、43 个独立算例。
- 知识正文和工具契约使用同一套来源、审阅和 digest 规则；公式、假设、舍入和边界算例都可核对。

## 为什么放在一个仓库

知识和工具回答的是同一类问题：“我该怎么跑、怎么补给、怎么判断这场训练或这条路线”。放在一个仓库里，读者可以从知识文章跳到相应工具，贡献者也能用同一套证据规范维护两类内容。工具站仍然独立，因为计算器和文件处理代码需要单独部署。

## 目录

```text
knowledge/
  content/zh-CN/{slug}.md          中文知识正文
  content/en/{slug}.md             英文知识正文
  data/entities/{slug}.json        主题、类型、来源引用
  data/sources/{sourceId}.json     来源与支持的结论
  data/reviews/{slug}.{locale}.json 审阅记录与 digest
tools/
  content/zh-CN/{slug}.md          中文工具说明
  content/en/{slug}.md             英文工具说明
  data/entities/{slug}.json        输入输出契约、公式、假设、舍入
  data/cases/{caseId}.json         独立算例
  data/sources/{sourceId}.json     标准、论文与公共指南
  data/reviews/{slug}.{locale}.json 审阅记录与 digest
```

两个子树各自保留完整的 `content/`、`data/`、`assets/` 结构，网站构建时分别作为知识根和工具根读取。

## 内容口径

- 每个实体只有一个主主题；辅助主题、人群和场景放在独立字段。
- 数值、效果和因果结论必须有可定位来源；研究结论、经验建议和个人推断分开写。
- 健康、伤病、孕产等具体干预建议需要相应专业审阅；没有审阅能力时保持草稿。
- 工具必须写清输入、运算顺序、单位、边界和舍入；修改计算口径要提升 `specVersion` 并同步算例。
- 中英文事实、限制和错误条件一致；不把机器翻译直接当英文成稿。

## 当前审阅状态

108 个实体均已完成 AI 辅助编辑审阅并发布（`published`，双语 `approve` 记录与匹配 digest）。审阅者是 `runmap-editorial`，明确标注为 AI 辅助，不是独立或专业医学/营养审阅。这个仓库不声称已经过专业审阅。

## 本地使用

内容由 `site-knowledge` 和 `site-tools` 构建时读取。六个工程位于同一父目录时，默认路径会自动指向 `running-handbook/knowledge` 与 `running-handbook/tools`；也可以用 `KNOWLEDGE_CONTENT_DIR`、`TOOLS_CONTENT_DIR` 覆盖。

本仓库没有安装或构建命令。内容校验、站点构建和搜索索引都在对应站点仓库完成。

## 许可与纠错

- 新写正文、工具说明与算例：CC BY 4.0，署名「跑起来 RunUp」。
- 第三方来源、引用、图片与链接材料：按各来源条件，逐项记录在实体或来源文件中。
- 网站代码：MIT，位于三个 `site-*` 仓库和 `paobu-core`。

发现事实、公式或来源问题时，请通过 Issue 或 Pull Request 说明具体段落、来源与建议修改。贡献流程见 [CONTRIBUTING.md](CONTRIBUTING.md)。

最后核对日期：2026-11-25。
