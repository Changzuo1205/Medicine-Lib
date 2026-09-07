---
type: system
status: active
tags:
  - system/log
---

# Change Log — 变更记录

记录 Medicine-Lib 的重大结构变化。

## 2026-08-10 — V1 初始化

- 创建 AGENTS.md（知识库规范 V1）
- 初始化目录骨架（00_Dashboard ～ 99_System）
- 创建首页 00_Dashboard/Home.md
- 创建 15 个知识节点模板（99_System/Templates/）
- 创建 16 个专科 MOC（07_MOCs/）
- 创建系统文件（README / Knowledge-Status / Source-Registry / Change-Log）
- 创建各目录 README 导航文件

## 记录规则

- 记录重大结构变化，不记录日常笔记修改
- 格式：`日期 — 变更摘要`
## 2026-09-07 — 免疫学概述 /ingest

- 注册讲座来源 `S-LEC-004`：`Medical Immunology Chapter 1 — 免疫学概述（杨艳艳，2026 秋）`
- 新建 Course：`[[08_Courses/Medical Immunology/Course|医学免疫学]]`
- 新建 Lecture：`[[08_Courses/Medical Immunology/Lectures/01 免疫学概述|01 免疫学概述]]`
- 新建 Physiology 概念：
  - `[[Immune System]]`（免疫系统组成与基本功能）
  - `[[Innate Immunity]]`（固有免疫）
  - `[[Adaptive Immunity]]`（适应性免疫 / 体液 + 细胞免疫）
- 新建 Pathophysiology 概念：
  - `[[Immune Dysregulation]]`（免疫异常与疾病 — 超敏 / 自身免疫 / 免疫缺陷 / 肿瘤）
- 所有新节点 `source_status: needs_review`（lecture-derived，待与权威教材逐句核对）
- 更新 [[Source-Registry]]（追加 S-LEC-004）

## 2026-09-07 — 03_Concepts 引入学科维度（以 Immunology 为首个学科目录）

> 用户反馈：03_Concepts 不应仅按"知识类型"组织（Physiology/Pathophysiology/Diseases…），还应支持"按学科"组织（Immunology/Cardiology/…）。本条目记录结构调整。

- **新增**：`03_Concepts/Immunology/`（首个按学科组织的子目录）
- **移动**：
  - `03_Concepts/Physiology/Immune System.md` → `03_Concepts/Immunology/Immune System.md`
  - `03_Concepts/Physiology/Innate Immunity.md` → `03_Concepts/Immunology/Innate Immunity.md`
  - `03_Concepts/Physiology/Adaptive Immunity.md` → `03_Concepts/Immunology/Adaptive Immunity.md`
  - `03_Concepts/Pathophysiology/Immune Dysregulation.md` → `03_Concepts/Immunology/Immune Dysregulation.md`
- **frontmatter 调整**：4 个节点统一新增 `tags: medicine/immunology`（保留原 `type` 字段与原有 tags）
- **新建**：`03_Concepts/Immunology/README.md`（学科目录导航）
- **更新**：`03_Concepts/README.md` — 引入"按学科 + 按知识类型"双轴组织原则，记录迁移规则
- **更新**：`08_Courses/Medical Immunology/Lectures/01 免疫学概述.md` — 修复因文件位置变化而失效的锚点链接
- **影响**：以上文件均为 lecture-derived，新增移动操作未改变实质医学内容；git 历史保留（git mv）

### 未来方向（待用户决策）

- 是否将其他学科（Cardiology、Nephrology、Endocrinology…）的知识也从 Physiology/Pathophysiology 迁移到各自的学科目录？
- 建议规则：当某学科的知识积累到 ≥3 个核心 concept 时，建立学科目录并迁移。
- 现阶段其他学科（Physiology 目录下的循环/肾/胃肠系，Pathophysiology 目录下的病理生理节点）维持原状，避免一次性大改动。

## 2026-09-07 — 03_Concepts V2：删除 Physiology/ 与 Pathophysiology/（按学科组织）

> 用户反馈：之前按"知识类型"组织的 `Physiology/` 与 `Pathophysiology/` 目录应该删除；只保留**已注册的学科目录**；以后知识点按学科分布。

### 重大变更

- **删除目录**：`03_Concepts/Physiology/`、`03_Concepts/Pathophysiology/`（连同 README）
- **归档（Archive）**：原目录下 **38 个医学节点**（25 Physiology + 13 Pathophysiology）移至 `99_System/Archive/Concepts-Retired/{Physiology,Pathophysiology}/` 作为"已废弃组织方式"存档
  - 包括：Cardiology 相关（13 个 cardiac/vascular Pathophysiology）、Nephrology 相关（17 个 renal Physiology）、Gastroenterology 相关（9 个 GI Physiology）
  - 这些内容**未删除**，仅从活跃知识层移至 Archive
- **保留目录**：`03_Concepts/Immunology/`（唯一的已注册学科）+ 跨学科"知识类型"目录（Diseases/Drugs/Procedures/Symptoms/Signs/Tests）

### 安全网说明

- Archive 中的节点保留了全部 frontmatter、链接、医学内容
- 将来注册新学科（Cardiology/Nephrology/Gastroenterology）时，可直接从 Archive 复活
- 如需**彻底删除** Archive 中的退役节点，请告知；目前保留作为可恢复存档

### 系统文件更新

- `03_Concepts/README.md` — 重写：移除 Physiology/Pathophysiology 目录说明，引入 V2 双轴组织原则
- `00_Dashboard/Home.md` — 重写：移除 39 节点列表，改为引用 Archive；新增"待注册学科候选"表
- `07_MOCs/Medicine MOC.md` — 替换 Pathophysiology 链接为 Immunology + Archive 链接
- `99_System/Templates/07_Pathophysiology.md` — 更新模板说明：病理生理节点必须放在已注册学科目录下
- `99_System/Knowledge-Status.md` — 更新节点数（5 active = 1 Disease + 4 Immunology）
- `99_System/Source-Registry.md` — 不变
- `01_Inbox/README.md` — 补充历史说明（节点已退役至 Archive）
- **`AGENTS.md`** — Section "03_Concepts" 改写为 V2：删除 Physiology/Pathophysiology 目录说明，加入"按学科组织"原则与"新建节点规则"

### 未变更

- `02_Raw/` — 原始 PDF 全部保留
- `04_Clinical/` — 暂未触及
- `06_Specialties/` 与 `07_MOCs/`（除 Medicine MOC 外）— 未触及
- `08_Courses/`（除已存在医学免疫学外）— 未触及

## 2026-09-07 — /study 免疫学概述

- 创建本次学习会话记录：`[[05_Study/Review/Session-2026-09-07-Immunology-Overview|/study Session — 免疫学概述]]`
- **新建 15 道题目**（`05_Study/Questions/Q-Imm-01 ~ 15`）：
  - Q-Imm-01 ~ 05：PPT 截图题转写（免疫系统组成、免疫应答不正确说法、中枢免疫器官、淋巴结功能、脾 T 细胞区）
  - Q-Imm-06 ~ 15：基于 Concept 节点的扩展题
    - Recall：Q-Imm-06（三大功能）、Q-Imm-07（适应性三大特点）
    - Interpretation：Q-Imm-08（WBC 分类解读）、Q-Imm-09（TCR αβ vs γδ）
    - Differential：Q-Imm-10（固有 vs 适应性时相）、Q-Imm-11（体液 vs 细胞免疫针对性）
    - Clinical Reasoning：Q-Imm-12（OPSI）、Q-Imm-13（HIV/CD4）、Q-Imm-14（MALT/sIgA）、Q-Imm-15（免疫异常四类匹配）
- **新建 10 张闪卡**（`05_Study/Flashcards/FC-Imm-01 ~ 10`）：关键事实速记（三大部分、三大功能、中枢器官、HSC 标志、T/B 区、中性粒数据、NK 标志、TCR/BCR、Th 亚群、免疫异常四类）
- **更新**：`[[08_Courses/Medical Immunology/Lectures/01 免疫学概述]]` — 课堂测试题块替换为指向 Q-Imm/FC-Imm 的链接列表
- **更新**：`[[08_Courses/Medical Immunology/Course]]` — 新增 "Reviews"、"Knowledge Gaps"、"相关学习材料" 三个章节
- **未触及**：所有 Concept 节点；原始 PDF；模板

## 2026-09-07 — 05_Study/Questions V2：清理未注册学科题目

> 用户反馈：未注册学科（Cardiology/Nephrology/Gastroenterology）的 Concept 节点已退役，相应题目也应同步清理。仅保留已注册学科 `[[03_Concepts/Immunology|Immunology]]` 对应的 `Q-Imm-*`。

### 操作

- **新建归档目录**：`99_System/Archive/Questions-Retired/{CircS2,Ur,GI}/`
- **移动 27 道非免疫学题目**至 Archive：
  - `Q-CircS2-01..10`（10 道，循环系统）→ `Archive/Questions-Retired/CircS2/`
  - `Q-Ur-01..15`（15 道，泌尿系统）→ `Archive/Questions-Retired/Ur/`
  - `Quiz-GI-Digestion-20260810.md`、`Quiz-GI-Digestion-02-20260810.md`（2 道，消化系统）→ `Archive/Questions-Retired/GI/`
- **保留**：`Q-Imm-01..15`（15 道，免疫学，唯一已注册学科）

### 文件内容

- 所有移动文件**字节完全保留**（未修改 frontmatter、题干、答案、解释、来源）
- 待对应学科注册时可直接从 Archive 复活

### 系统文件更新

- `[[05_Study/Questions/README|Questions README]]` — 移除非免疫学题目的活跃清单；新增"退役题目（未注册学科）"章节，说明 Archive 位置与复活条件
- `[[00_Dashboard/Home|Dashboard]]` — 练习题数量从 27 改为 "15 活跃；27 退役"
- 其他 README（Flashcards / Review）无需更新（无相关引用）

### 安全网

- Archive 文件 `99_System/Archive/Questions-Retired/` 完全保留，**未真正删除**
- 如需彻底删除，请告知
