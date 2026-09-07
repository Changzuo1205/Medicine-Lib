---
type: dashboard
status: active
tags:
  - system/dashboard
created: 2026-08-10
last_refresh: 2026-09-07
---

# 🏥 Medicine-Lib

> 临床医学生个人医学知识库 · V2（按学科组织）
> 遵循 [[AGENTS.md]] 规范维护。

## 知识库当前状态

| 区域 | 状态 | 备注 |
|------|------|------|
| AGENTS.md 规范 | ✅ 已就绪 | 32 节规则完整；V2 起改用"按学科组织" |
| 目录骨架 | ✅ 已就绪 | 00–07 + 99 + 08_Courses |
| 已注册学科 | 1 | `[[03_Concepts/Immunology/README\|Immunology]]` |
| 知识节点 | ✅ 已创建 | 1 Disease · 4 Immunology = **5 节点**（active 状态） |
| 退役存档 | 38 节点 | 见 [[99_System/Archive/Concepts-Retired/\|Concepts-Retired]]（按学科注册时可复活） |
| 原始资料 | ✅ 部分导入 | 5 份课程 PDF 在 `02_Raw/Lectures/`（Circulation §2/§3、Urine 2026 春、GI Digestion、免疫学绪论） |
| 临床推理材料 | ⚠️ 尚未创建 | `04_Clinical/` 全部子目录空 |
| 学习材料 | ✅ 部分创建 | 27 道题（10 CircS2 + 12 Ur + 3 Ur Review Set + 2 Quiz）；Flashcards / Wrong-Answers / Review 仍空 |
| 模板 | ✅ 已就绪 | 20 套模板在 `99_System/Templates/` |
| 系统日志 | ✅ 已就绪 | Knowledge-Status / Source-Registry / Change-Log / Textbook-Import-SOP / Archive |

## 核心知识入口（按学科）

### 已注册学科

- [[03_Concepts/Immunology/README|Immunology]] — 免疫学（4 节点）
  - [[Immune System]] · [[Innate Immunity]] · [[Adaptive Immunity]] · [[Immune Dysregulation]]

### 待注册的学科候选（基于已退役知识，未来按需注册）

> 当积累足够概念时（建议阈值 ≥3 个核心 concept），可创建学科目录并从 Archive 复活内容。
> 当前候选：

| 候选学科 | 候选依据（来自 Archive） | 建议目录 |
|----------|-------------------------|----------|
| Cardiology | 心脏/血管/循环相关 13 个 Pathophysiology 节点 | `[[03_Concepts/Cardiology/README\|Cardiology]]` |
| Nephrology | 泌尿/水电解质 17 个 Physiology 节点 | `[[03_Concepts/Nephrology/README\|Nephrology]]` |
| Gastroenterology | 消化/吸收 9 个 Physiology 节点 | `[[03_Concepts/Gastroenterology/README\|Gastroenterology]]` |

### 跨学科"知识类型"目录（保留 — Disease 节点按知识类型组织，不按学科）

- [[03_Concepts/Diseases/README|Diseases]] — 疾病（1）
- [[03_Concepts/Drugs/README|Drugs]] — 药物（0）
- [[03_Concepts/Procedures/README|Procedures]] — 操作（0）
- [[03_Concepts/Symptoms/README|Symptoms]] — 症状（0）
- [[03_Concepts/Signs/README|Signs]] — 体征（0）
- [[03_Concepts/Tests/README|Tests]] — 检查（0）

> ⚠️ V1 中的 `Physiology/` 与 `Pathophysiology/` 已废弃删除（见 [[Change-Log]] 2026-09-07 第三条）。所有生理/病理生理内容必须放在**已注册学科目录下**，且 `frontmatter.type` 仍标识 `physiology` 或 `pathophysiology`。

### 退役存档（仅供历史回溯，不属于活跃知识）

- [[99_System/Archive/Concepts-Retired/Physiology/README-Original|Archive: Physiology]]（25 节点 + 1 README）
- [[99_System/Archive/Concepts-Retired/Pathophysiology/README-Original|Archive: Pathophysiology]]（13 节点 + 1 README）

## 临床知识入口

- [[04_Clinical/Differential/README|Differential]] — 鉴别诊断（0）
- [[04_Clinical/Algorithms/README|Algorithms]] — 临床决策流程（0）
- [[04_Clinical/Cases/README|Cases]] — 病例（0）
- [[04_Clinical/Clinical-Pearls/README|Clinical Pearls]] — 临床要点（0）

## 学习系统入口

- [[05_Study/Questions/README|Questions]] — 练习题（15 活跃；27 退役，见 `[[99_System/Archive/Questions-Retired/|Questions-Retired]]`）
- [[05_Study/Wrong-Answers/README|Wrong Answers]] — 错题（0）
- [[05_Study/Flashcards/README|Flashcards]] — 闪卡（0）
- [[05_Study/Review/README|Review]] — 复习（0）

## 专科入口

- ✅ Active：[[Nephrology MOC]]
- 🔜 Stub（待填充）：
  [[Cardiology MOC]] · [[Respiratory MOC]] · [[Gastroenterology MOC]] · [[Endocrinology MOC]] · [[Neurology MOC]] · [[Infectious Disease MOC]] · [[Hematology MOC]] · [[Oncology MOC]] · [[Surgery MOC]] · [[Pediatrics MOC]] · [[Obstetrics-Gynecology MOC]] · [[Psychiatry MOC]] · [[Dermatology MOC]] · [[Emergency Medicine MOC]]

## MOC 入口

- [[Medicine MOC]] — 医学总导航

## 最近学习

_（尚无内容 — 学习活动开始后在此记录）_

## Knowledge Gaps

以下区域**完全为空**，是知识库当前最显著的缺口：

| 缺口类型 | 目录 | 优先级建议 |
|----------|------|-----------|
| 症状/体征/检查节点 | `03_Concepts/Symptoms/` · `Signs/` · `Tests/` | 高（临床推理前置条件） |
| 药物节点 | `03_Concepts/Drugs/` | 高 |
| 操作/治疗节点 | `03_Concepts/Procedures/` | 中 |
| 免疫学子节点 | `03_Concepts/Immunology/` 内"待建"清单 | 高（详见 [[03_Concepts/Immunology/README\|Immunology README]]） |
| 鉴别诊断 | `04_Clinical/Differential/` | 高 |
| 临床算法 | `04_Clinical/Algorithms/` | 高 |
| 病例 | `04_Clinical/Cases/` | 中 |
| 临床要点 | `04_Clinical/Clinical-Pearls/` | 中 |
| 错题本 | `05_Study/Wrong-Answers/` | 中 |
| 闪卡 | `05_Study/Flashcards/` | 中 |
| 复习队列 | `05_Study/Review/` | 中 |

详见 [[99_System/Knowledge-Status|Knowledge Status]]。

## Review

_（尚无内容 — 复习队列见 [[05_Study/Review/README|Review]] 与 [[99_System/Knowledge-Status|Knowledge Status]]）_

## 系统

- [[99_System/README|System 说明]]
- [[99_System/Source-Registry|Source Registry]] — 来源登记
- [[99_System/Change-Log|Change Log]] — 变更记录
- [[99_System/Knowledge-Status|Knowledge Status]] — 缺口/待审/冲突跟踪
- [[99_System/Archive/Concepts-Retired/|Concepts Retired Archive]] — 已退役概念存档

---

_Last dashboard refresh: 2026-09-07_