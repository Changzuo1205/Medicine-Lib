---
type: lecture
status: active
course: "[[../Course]]"
chapter:                 # 阿拉伯数字，如 2（不要写"第二章"）
date:                    # 如 2026 秋
instructor:
topics:
  -
aliases:                 # 建议：本章中文名 + 学科内惯用别名，便于概念节点回链
  - {{第N章}}
  - {{章节中文名}}
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

## 本章知识导航（{{N}} 个概念节点）

> 本章概念节点的**分组索引与要点速查**。概念知识本体存放于 [[../../../03_Concepts/{{学科}}/README|03_Concepts/{{学科}}]]。
> **章节导航的唯一归属就是本节** —— 不在 `03_Concepts/` 下另建 `Chapter N - ….md`（Ingest-SOP §3.5.5）。

### 一、{{分组名}} — {{n}} 个节点

| 概念 | type | 要点 |
|------|------|------|
| [[{{概念节点}}]] {{中文名}} | pathophysiology | {{一句话要点}} |

---

## 第一节 {{节标题}}

{{按讲义结构逐节展开；正文内直接链接概念节点}}
{{不要写 `> 详见 [[MOC#…]]` 之类的指针 —— 章节导航已在本文件上方}}

---

## Class Notes

> [!note] 源文本特点
> {{讲义体裁、结构完整性、有无节标题等}}

> [!question] 我的疑问（待 review 解决）
> {{对讲义表述的疑问}}

> [!ai] AI 补充（必须核实来源）
> {{讲义未覆盖、需另找来源的部分；必须标记 evidence_level 与 source_status}}

## Knowledge Gaps（待建 / 需扩展）

### 本章未建 / 需补充

- [ ] {{待建节点}}

### 跨学科联动（待其他学科注册后建立）

- [ ] {{跨学科节点}}

## Related Medical Knowledge

- 上一章：[[{{上一章 Lecture 文件名}}|{{上一章标题}}]]
- 下一章：[[{{下一章 Lecture 文件名}}|{{下一章标题}}]]
- 学科导航：[[../../../03_Concepts/{{学科}}/README|{{学科}} 学科目录]] · [[../Course|{{课程名}} Course]]
- 协作学科：[[../../../03_Concepts/{{协作学科}}/README|{{协作学科}}]]
- 原始课件：[[../../../02_Raw/Lectures/{{学科}}/README|02_Raw/Lectures/{{学科}}]]

## Related Questions

_（暂无；后续 /quiz 阶段生成）_

## 来源与摄入记录

- 主来源：[[../../../02_Raw/Lectures/{{学科}}/{{文件名}}|{{来源标题}}]] — {{覆盖节次}}
- 来源登记：[[../../../99_System/Source-Registry#S-LEC-NNN|S-LEC-NNN]]
- evidence_level: C（医学教育资料 / 课程笔记）；source_status: needs_review
- **待核对**：{{教材版本与章节}}

### /ingest 完成状态（YYYY-MM-DD）

- **已建概念节点**：{{N}} 个（{{分组明细}}）
- **章节导航**：写在本 Lecture 内；`03_Concepts/{{学科}}/` 只存概念节点

---

<!--
检查清单（见 Ingest-SOP §3.5.3 / §3.5.4 / §3.5.5 / §5.1.7）：
- [ ] 文件名 = <两位数章节号> <中文章节名>.md，且与 Course.md 引用逐字一致
- [ ] course: "[[../Course]]"、chapter 为阿拉伯数字
- [ ] 含 来源 callout / Lecture Overview / 章节目标 / 章节结构 / 本章知识导航 /
      Knowledge Gaps / 各节正文 / Class Notes / Related Medical Knowledge /
      Related Questions / 来源与摄入记录
- [ ] `## 本章知识导航` 的分组标题数字 = 各组表格实际行数
- [ ] 概念节点已回链本 Lecture（`## Related Concepts` 首行）
- [ ] Course.md 的 `## Lectures` 清单与节点计数已回写
- [ ] **本文件是章节导航的唯一归属**：03_Concepts/ 下不得出现 Chapter N - ….md
-->
