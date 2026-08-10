---
type: processing_record
status: active
source_file: "02_Raw/Lectures/消化和吸收-2026.pdf"
processed_date: 2026-08-10
tags:
  - system/processing
---

# Processing Record — GI Function: Digestion and Absorption

## 原始资料（Course Context Source）

| 项目 | 内容 |
|------|------|
| 文件名 | 消化和吸收-2026.pdf |
| 位置 | `02_Raw/Lectures/`（原始文件未移动、未修改） |
| 类型 | 课程 PPT / 讲义 |
| 主题 | Gastrointestinal Function: Digestion and Absorption（消化和吸收） |
| 讲师 | 杜希恂 |
| 时间标注 | 2026 |
| 页数 | 130 |
| 课程归属 | 未知（待用户提供真实课程名称） |

## 处理方式

/ingest 标准流程：Raw Material → Extract → Identify Concepts → Find Existing Nodes → Create/Update → Add Links → Record Sources → Audit。

- 知识点全部为**正常生理学** → 按结构性检查决策，新建 Concept 进入 `03_Concepts/Physiology/`（20_Physiology 模板，type: physiology）
- 已有 13 个 Concept 均为循环系统，与消化系统无重叠，无复用/重复风险
- 未修改 AGENTS.md

## 产出清单

- [[Lecture-GI-Digestion-and-Absorption]] — Lecture（暂存 Inbox，待课程名确认后移入 08_Courses/）
- 9 个新 Concept（03_Concepts/Physiology/）
- Source-Registry 更新（登记讲义来源）

## 待办

- [ ] 用户确认课程名称 → Lecture 移入 08_Courses/<Course>/Lectures/ 并创建 Course.md
- [ ] 讲义内容与教材核对（source_status 从 needs_review 提升）