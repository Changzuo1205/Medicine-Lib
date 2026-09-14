---
type: system
status: active
last_updated: 2026-09-14
tags:
  - system/status
---

# Knowledge Status — 知识状态

用于跟踪知识库中需要关注的知识。

## 摘要（2026-09-14 /ingest 病理学第二章后更新）

- **V2 结构**：`Physiology/` 与 `Pathophysiology/` 已退役（存档 38 个概念节点 + 2 份原 README），活跃概念节点 100
- **活跃概念节点**：100 = 学科节点 99（16 Immunology · 7 Medical Microbiology · 17 Clinical Epidemiology · 11 Human Parasitology · **48 Pathology**）+ 跨学科目录 1（Diseases）
- **已注册学科**：5（`[[03_Concepts/Immunology|Immunology]]` · `[[03_Concepts/Medical Microbiology|Medical Microbiology]]` · `[[03_Concepts/Human Parasitology|Human Parasitology]]` · `[[03_Concepts/Clinical Epidemiology|Clinical Epidemiology]]` · `[[03_Concepts/Pathology|Pathology]]`）
- **已摄入讲座**：12 份（含免疫学 2 讲：免疫学概述、抗原；病理学 2 讲：第一/二章）
- **已注册来源**：12 个讲座 ID（S-LEC-001 ~ 012，见 [[Source-Registry]]）；最近新增 S-LEC-012 = Pathology Chapter 2（损伤的修复）
- **已注册教材**：4 份（S-TXT-001 ~ 004，见 [[Source-Registry]]；均为 `reference-only / not-ingested`）
- **学习材料（本次 /study 后）**：
  - Questions：**15 活跃**（Q-Imm-01 ~ 15，仅 Immunology）— 详见 `[[05_Study/Questions/README|Questions]]`
  - Flashcards：**10 张**（FC-Imm-01 ~ 10）— 详见 `[[05_Study/Flashcards/README|Flashcards]]`
  - Review Session：**1 个**（`Session-2026-09-07-Immunology-Overview`）— 详见 `[[05_Study/Review/README|Review]]`
  - Wrong-Answers：0（首次 /study，尚未产生错题）
- **Source Status**：全部 100 节点 `source_status: needs_review`（lecture-derived，待与权威教材核实）
- **退役题目**：27 道（Q-CircS2-01..10 + Q-Ur-01..15 + Quiz-GI-* x 2）— 已移至 `[[99_System/Archive/Questions-Retired/|Questions-Retired]]`，对应未注册学科（Cardiology/Nephrology/Gastroenterology）注册时可复活
- **Knowledge Gaps**：见 [[03_Concepts/Immunology/README|Immunology README]] 与 [[03_Concepts/Pathology/README|Pathology README]] 的待建清单；病理学第三章起（局部血液循环障碍 / 炎症 / 肿瘤 / 免疫病理）尚未摄入

## Knowledge Gaps

_（暂无具体条目 — 见 Dashboard 的 Knowledge Gaps 表格）_

| 日期 | 主题 | 缺口描述 | 来源需求 | 状态 |

## Needs Review

_（暂无 — 全部 lecture-derived 节点均带 `source_status: needs_review` 标记，但未单独列）_

| 日期 | 节点 | 原因 | 优先级 | 状态 |

## Conflicting Evidence

_（暂无）_

| 日期 | 节点 | Source A | Source B | 差异 | 处理状态 |

## Unsourced Knowledge

_（暂无）_

| 日期 | 节点 | 内容 | 状态 |

## Outdated Knowledge

_（暂无）_

| 日期 | 节点 | 原因 | 状态 |

## 使用说明

- 每次 /audit 或 /review 后更新本文件
- 证据不足、来源冲突、内容可能过时时，标记 Needs Review 而不是删除
- 冲突来源不擅自取舍，建立 Evidence Conflict 说明后等待人工复核
