---
type: lecture
status: active
course: "[[../Course]]"
chapter:                 # 阿拉伯数字，如 2（不要写"第二章"）
discipline:              # 学科名，与 03_Concepts/<学科>/ 目录名一致
date:                    # 如 2026 秋
instructor:
topics:
  -
---

# {{NN}} {{章节名}}

> [!info] 来源
> - 原始资料：[[../../../02_Raw/Lectures/{{学科}}/{{文件名}}]]
> - 讲者：
> - 来源登记：[[../../../99_System/Source-Registry#S-LEC-NNN|S-LEC-NNN]]
> - 知识状态：Source-derived lecture，尚未对正文逐句核对教材原文 → `source_status: needs_review`
> - 关联学科：[[../../../03_Concepts/{{学科}}/README|{{学科}}]]

## Lecture Overview

{{本讲在课程中的位置与主线，2–4 句}}

## 章节目标

> [!info] Clinical Reasoning
> 本节为**推断的学习层级**。若原始讲义未标注掌握程度，必须保留本标注（AGENTS.md §26）——
> 不要把推断当成来源直接陈述。

| 层级 | 要求 | 内容 |
|------|------|----------|
| 掌握 | 必须掌握 | |
| 熟悉 | 应熟悉 | |
| 了解 | 一般了解 | |

## 章节结构

```
{{本章在学科中的位置：流程 / 关系图}}
```

---

## 第一节 {{节标题}}

{{按讲义结构逐节展开；正文内直接链接概念节点}}
{{不要写 `> 详见 [[MOC#…]]` 这类指针；也不要在这里放节点要点表 —— 那是学科 README 的职责}}

---

## Class Notes

> [!note] 源文本特点
> {{讲义体裁、结构完整性、有无节标题等}}

> [!question] 我的疑问（待 review 解决）
> {{对讲义表述的疑问}}

> [!ai] AI 补充（必须核实来源）
> {{讲义未覆盖、需另找来源的部分；必须标记 evidence_level 与 source_status}}

## Related Medical Knowledge

{{本章**全部概念节点**的扁平清单 —— 与其他学科的 Lecture 一致}}

- [[{{概念节点 1}}]]
- [[{{概念节点 2}}]]
- {{可再附 1–2 条：上一章 / 下一章 Lecture、协作学科}}

## Related Questions

_（暂无；后续 /quiz 阶段生成）_

---

<!--
检查清单（见 Ingest-SOP §3.5.3 / §3.5.4 / §3.5.5 / §5.1.7）：
- [ ] 文件名 = <两位数章节号> <中文章节名>.md，且与 Course.md 引用逐字一致
- [ ] frontmatter：course: "[[../Course]]"、chapter 为阿拉伯数字、discipline 填学科名
- [ ] 小节集合与其他学科一致：Lecture Overview / 章节目标 / [章节结构] /
      各节正文 / Class Notes / Related Medical Knowledge / Related Questions
- [ ] **本 Lecture 不自创小节**：不写 `## 本章知识导航` / `## Knowledge Gaps` /
      `## 来源与摄入记录`（内容分别归学科 README / Course.md / 顶部来源 callout）
- [ ] `## Related Medical Knowledge` = 本章全部概念节点的扁平清单
- [ ] 概念节点已回链本 Lecture（`## Related Concepts` 首行）
- [ ] 学科 README 的「已建节点」索引（分组 + 要点）已同步，分组数字 = 表内行数
- [ ] 所有相对路径以**实例化后的位置**（08_Courses/<学科>/Lectures/）为准，且不逃出 vault
- [ ] Course.md 的 `## Lectures` 清单与节点计数已回写
-->
