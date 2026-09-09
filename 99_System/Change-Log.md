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

## 2026-09-07 — 注册新学科：病原与感染性疾病 Ⅰ

> 用户反馈：注册"病原与感染性疾病 Ⅰ"为新学科。这是 V2 重构后**第二个**已注册学科。

### 操作

- **新建学科目录**：`03_Concepts/Infectious Disease/`
- **新建 README**：`03_Concepts/Infectious Disease/README.md` — 包含学科范围（病原生物学 / 抗感染免疫 / 各系统感染性疾病 / 抗感染药物 / 诊断）、待建节点清单（病原 / 疾病 / 药物 / 机制 / 检查 / 算法 / 病例）、使用规则

### 文件结构

```
03_Concepts/
├── Immunology/                        ← 已注册学科 1（4 节点）
└── Infectious Disease/                ← 已注册学科 2（0 节点，待 /ingest）
    └── README.md
```

### 系统文件更新

- `[[00_Dashboard/Home|Dashboard]]` — 顶部统计"已注册学科"改为 2；新增 Infectious Disease 条目与 Knowledge Gaps 行
- `[[07_MOCs/Medicine MOC|Medicine MOC]]` — 新增 `Infectious Disease` 链接
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 更新已注册学科数

### 与现有结构的关系

- 与 `[[06_Specialties/Infectious Disease/README|06_Specialties/Infectious Disease]]`（专科导航）共存 — 专科导航保留 06 层职责
- 与 `[[Infectious Disease MOC]]`（导航页）共存 — MOC 在 07 层，学科在 03 层
- 与 `[[03_Concepts/Immunology|Immunology]]` 协作 — 免疫学概念放 Immunology；本学科只放感染相关免疫应用（如免疫逃逸、疫苗等）

### 待 /ingest

- 等用户提供病原与感染性疾病 Ⅰ 的课程 PPT / 教材后，按 `/ingest` 流程建立具体 Concept 节点
- README 中已列出待建节点清单（按病原 / 疾病 / 药物 / 机制 / 检查 / 算法 / 病例分类）

## 2026-09-07 — /ingest 病原与感染性疾病Ⅰ 绪论 + 第1章 细菌的形态与结构

> 用户对刚注册的 `[[03_Concepts/Infectious Disease|Infectious Disease]]` 学科执行首次 /ingest。原始资料：`02_Raw/Lectures/Medical Microbiology/1 绪论.pdf`（36 页）+ `02_Raw/Lectures/Medical Microbiology/1 2 第1章 细菌的形态与结构 1.pdf`（16 页），讲者赵巍（病原生物学教研室）。

### 注册讲座来源

- `S-LEC-005` — 《绪论》（赵巍，2026 秋）
- `S-LEC-006` — 《第1章 细菌的形态与结构》（赵巍，2026 秋）

### Created（Course / Lecture 层）

- `[[08_Courses/Pathogen and Infectious Diseases I/Course|病原与感染性疾病Ⅰ Course]]`
- `[[08_Courses/Pathogen and Infectious Diseases I/Lectures/01 绪论|01 绪论 Lecture]]`
- `[[08_Courses/Pathogen and Infectious Diseases I/Lectures/02 细菌的形态与结构|02 细菌的形态与结构 Lecture]]`

### Created（Concept 层 — 全部放在 `03_Concepts/Infectious Disease/`）

| 节点 | type | 核心内容 |
|------|------|----------|
| [[Medical Microbiology]] | pathophysiology | 学科定义、研究对象（病原体三大类）、学科任务（病原学/致病机制/诊断防治） |
| [[Microbial Classification]] | pathophysiology | 微生物三大类对比（大小、细胞结构、细胞器、细胞核、核酸、能量代谢） |
| [[Infection vs Transmission]] | pathophysiology | 感染 vs 传染的关键区分；耳源性脑膜炎 vs 流脑 |
| [[Koch's Postulates]] | pathophysiology | 郭霍法则经典四条件 + 现代修正原因 + Fredericks 1996 修正案 |
| [[Bacterium]] | pathophysiology | 细菌定义（两大特征：原始核质 + 肽聚糖）+ 广义 vs 狭义 + 6 类原核细胞型微生物 |
| [[Bacterial Morphology]] | pathophysiology | μm 测量 + 三种基本形态 + 球菌排列 + 螺形菌 4 属 + 典型 vs 衰退型 |
| [[Bacterial Structure]] | pathophysiology | 基本结构（4 种）+ 特殊结构（4 种）+ 革兰染色临床意义 + L 型菌 + 芽胞 |

### Updated

- `[[99_System/Source-Registry|Source-Registry]]` — 追加 S-LEC-005/006
- `[[00_Dashboard/Home|Dashboard]]` — 顶部统计更新（学科已注册 2、活跃节点 +7 = 12）
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 摘要更新（Infectious Disease 7 节点）

### 未变更

- `02_Raw/Lectures/Medical Microbiology/1 绪论.pdf`、`02_Raw/Lectures/Medical Microbiology/1 2 第1章 细菌的形态与结构 1.pdf` — 未修改
- `AGENTS.md` — 未修改
- `03_Concepts/Immunology/` — 未触及

### 待 /ingest 后续章节

- 第2章 细菌的生理（生长繁殖、代谢、遗传变异）
- 第3章 细菌的致病性与抗感染免疫
- 第4-14 章：各类细菌（球菌、杆菌、螺形菌、放线菌、支原体、衣原体、立克次体、螺旋体）
- 第15章+：真菌、寄生虫

## 2026-09-08 — 学科拆分：病原与感染性疾病Ⅰ → 医学微生物学 + 人体寄生虫学

> 用户反馈：将"病原与感染性疾病Ⅰ"按学科本质拆分为两个独立学科：**医学微生物学（Medical Microbiology）** + **人体寄生虫学（Human Parasitology）**。原课程包含 微生物（44 课时）+ 寄生虫（22 课时）= 66 课时。

### 拆分前后

| | 拆分前 | 拆分后 |
|---|--------|--------|
| 课程 | 病原与感染性疾病Ⅰ | 医学微生物学 + 人体寄生虫学 |
| 学科目录 | `03_Concepts/Infectious Disease/` | `03_Concepts/Medical Microbiology/` + `03_Concepts/Human Parasitology/` |
| Course 目录 | `08_Courses/Pathogen and Infectious Diseases I/` | `08_Courses/Medical Microbiology/` + `08_Courses/Human Parasitology/` |

### 操作

#### Concept 层

- **新建** `03_Concepts/Medical Microbiology/` 学科目录
- **新建** `03_Concepts/Human Parasitology/` 学科目录
- **移动 7 个 Concept 节点**（全部属于微生物学）：
  - Medical Microbiology · Microbial Classification · Infection vs Transmission · Koch's Postulates · Bacterium · Bacterial Morphology · Bacterial Structure
  - 起点：`03_Concepts/Infectious Disease/` → 终点：`03_Concepts/Medical Microbiology/`
- **更新 7 个文件的 frontmatter**：将 `tags: medicine/infectious-disease` 改为 `medicine/medical-microbiology`
- **新建** `03_Concepts/Medical Microbiology/README.md`（专注微生物学范围）
- **新建** `03_Concepts/Human Parasitology/README.md`（专注寄生虫学范围）
- **删除** 空目录 `03_Concepts/Infectious Disease/`

#### Course 层

- **移动 Course**：`Pathogen and Infectious Diseases I/Course.md` → `Medical Microbiology/Course.md`
- **移动 2 个 Lectures**：`Pathogen and Infectious Diseases I/Lectures/{01 绪论, 02 细菌的形态与结构}.md` → `Medical Microbiology/Lectures/`
- **更新 Course 与 Lectures**：标题改为"医学微生物学"；补充拆分说明；添加 `discipline: Medical Microbiology` 字段
- **新建** `08_Courses/Human Parasitology/Course.md`（空课程，待 /ingest）
- **删除** 空目录 `Pathogen and Infectious Diseases I/`

### 系统文件更新

- `[[00_Dashboard/Home|Dashboard]]` — 已注册学科 2→3；活跃节点统计更新；Knowledge Gaps 拆分两行
- `[[07_MOCs/Medicine MOC|Medicine MOC]]` — 拆分两行（Medical Microbiology + Human Parasitology）
- `[[07_MOCs/Infectious Disease MOC|Infectious Disease MOC]]` — 顶部说明拆分；分"微生物学"和"寄生虫学"两个 section 引用
- `[[AGENTS.md|AGENTS]]` — 已注册学科列表更新（2 → 3 个）
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 已注册学科数更新

### 未变更

- 原始 PDF（`02_Raw/Lectures/Medical Microbiology/1 绪论.pdf`、`1 2 第1章 细菌的形态与结构 1.pdf`）— 未修改
- Source Registry 的 `S-LEC-005/006` — 保持原文件名不变（按 Source-Status 原则，**重新 ingest 时再注册新的寄生虫学章节**）
- 06_Specialties/Infectious Disease/ — 临床专科导航保留（与学科拆分无关）

### 待 /ingest

- 等用户提供寄生虫学章节 PPT / 教材后，执行 `/ingest 人体寄生虫学 第X章`
- `03_Concepts/Human Parasitology/README.md` 已列出完整待建节点清单（蠕虫 / 原虫 / 节肢动物 / 寄生虫病 / 抗寄生虫药 / 检查 / 算法 / 病例）

## 2026-09-09 — 注册新学科：临床流行病学（Clinical Epidemiology）

> 用户反馈：注册"临床流行病学"作为第 4 个已注册学科。同时 `02_Raw/Lectures/` 下新增两份临床流行病学 PPTX 原始资料。

### 操作

- **新建学科目录**：`03_Concepts/Clinical Epidemiology/`
- **新建 README**：`03_Concepts/Clinical Epidemiology/README.md` — 包含学科范围（流行病学基础、病因与因果、研究设计、偏倚与混杂、诊断试验评价、治疗效果评价、预后研究、系统综述/Meta 分析、EBM、公共卫生监测）、待建节点清单、使用规则

### 02_Raw/Lectures 更新

- **新增文件**（2 份 PPTX）：
  - `02_Raw/Lectures/Clinical Epidemiology/流行病学绪论.pdf`（4.4 MB）
  - `02_Raw/Lectures/Clinical Epidemiology/疾病的分布.pdf`（5.1 MB）
- **更新 `02_Raw/Lectures/README.md`** — 重新组织为**按学科分组**的清单：
  - 医学微生物学（3 份）
  - 免疫学（1 份）
  - 临床流行病学（2 份）— 含 PPTX ⚠标注
  - 人体寄生虫学（0 份，待补充）
  - 基础学科（前期讲座 — Circulation / Urine / Digestion）
- **待办项**：
  - 注册 `S-LEC-007/008`（待用户 /ingest）
  - 安装 `python-pptx` 库（当前工具基于 pypdf，无法直接提取 PPTX）
  - 提供临床流行病学后续章节
  - 提供人体寄生虫学第 1 章及后续章节

### 系统文件更新

- `[[00_Dashboard/Home|Dashboard]]` — 已注册学科 3→4；Knowledge Gaps 新增临床流行病学行
- `[[07_MOCs/Medicine MOC|Medicine MOC]]` — 新增 Clinical Epidemiology 链接
- `[[AGENTS.md|AGENTS]]` — 已注册学科列表（3 → 4）
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 已注册学科数（3 → 4）

### 未变更

- 原始 PDF/PPTX 文件 — 未修改
- 现有 Concept 节点 — 未触及
- Source Registry（`S-LEC-005/006`）— 未变更；待 /ingest 时再登记新章节

### 待 /ingest

- 等用户执行 `/ingest 临床流行病学 绪论`（或类似指令），时再执行完整 ingest 流程
- README 已列出完整待建节点清单（按 10 个主题分组）

## 2026-09-09 — /ingest 临床流行病学 绪论 + 疾病的分布

> 用户反馈：对刚注册的 `[[03_Concepts/Clinical Epidemiology|Clinical Epidemiology]]` 学科执行首次 /ingest。原始资料：`02_Raw/Lectures/Clinical Epidemiology/流行病学绪论.pdf`（91 张）+ `02_Raw/Lectures/Clinical Epidemiology/疾病的分布.pdf`（109 张），讲者栗世如（公共卫生学院流行病与卫生统计学系）。

### 工具确认

- **python-pptx 已安装**（版本 1.0.2）→ 可直接提取 PPTX 内容
- 本次 /ingest 共处理 **200 张 PPT（91 + 109）**

### 注册讲座来源

- `S-LEC-007` — 《流行病学绪论》（栗世如，2026 秋）
- `S-LEC-008` — 《疾病的分布》（栗世如，2026 秋）

### Created（Course / Lecture 层）

- `[[08_Courses/Clinical Epidemiology/Course|临床流行病学 Course]]`
- `[[08_Courses/Clinical Epidemiology/Lectures/01 流行病学绪论|01 流行病学绪论 Lecture]]`
- `[[08_Courses/Clinical Epidemiology/Lectures/02 疾病的分布|02 疾病的分布 Lecture]]`

### Created（Concept 层 — 全部放在 `03_Concepts/Clinical Epidemiology/`）

| 节点 | type | 核心内容 |
|------|------|----------|
| [[Epidemiology]] | pathophysiology | 学科定义、三个层次、三个阶段、三种方法、三大要素 |
| [[History of Epidemiology]] | pathophysiology | 3 阶段 + 关键人物（Hippocrates / Lind / Jenner / Snow / Pasteur / Koch / Doll & Hill / Framingham / INCLEN） |
| [[Disease Frequency Measures]] | pathophysiology | 测量指标总览（发病 / 患病 / 死亡 + 6 项子指标） |
| [[Incidence Rate]] | pathophysiology | 三要素 + 平均人口数 + 标准化处理 |
| [[Prevalence]] | pathophysiology | 时点/期间患病率 + 患病率=发病率×病程 公式 |
| [[Mortality Rate]] | pathophysiology | 粗死亡率 + 标化死亡率 + 死亡专率 |
| [[Case Fatality Rate]] | pathophysiology | 与死亡率区别 + SARS 6.55% / 埃博拉 55% |
| [[Survival Rate]] | pathophysiology | 1/3/5 年生存率 + 与病死率区别 |
| [[Disease Distribution]] | pathophysiology | 三间分布（人间/时间/空间）总览 |
| [[Epidemic Intensity]] | pathophysiology | 散发/暴发/流行/大流行 + 暴发 vs 短期波动 |
| [[Distribution by Population]] | pathophysiology | 年龄/性别/职业/民族/婚姻/行为/流动人口 + 横断面 vs 出生队列分析 |
| [[Distribution by Time]] | pathophysiology | 短期波动/季节性/周期性/长期趋势 + 伦敦大雾案例 |
| [[Distribution by Place]] | pathophysiology | 国家间/城乡/聚集性/地方性 + 三类地方性 + 输入性疾病 |
| [[Migration Epidemiology]] | pathophysiology | 移民流行病学方法学 + 日本移民胃癌经典研究 |
| [[Clinical Epidemiology (concept)\|Clinical Epidemiology]] | pathophysiology | 1938 John Paul 提出；1982 INCLEN；DME 三要素 |
| [[Evidence-Based Medicine]] | pathophysiology | "证据在哪里？" + PICO 框架 + 证据等级金字塔 |
| [[Meta-Analysis]] | pathophysiology | 累积 20万+ RCT 的系统总结；PRISMA；森林图 / 漏斗图 |

### Updated

- `[[99_System/Source-Registry|Source-Registry]]` — 追加 S-LEC-007/008
- `[[00_Dashboard/Home|Dashboard]]` — 节点数 12 → 29（+17 Clinical Epidemiology）
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 已注册学科仍 4；活跃节点 12 → 29

### 未变更

- `02_Raw/Lectures/*.pptx` — 未修改
- `AGENTS.md` — 未修改
- `03_Concepts/{Immunology, Medical Microbiology, Human Parasitology}/` — 未触及

### 待 /ingest 后续章节

- 病因与因果推断（Hill 标准）
- 研究设计（描述性 / 病例对照 / 队列 / RCT）
- 偏倚与混杂（3 大类 35 种偏倚）
- 诊断试验评价（Se / Sp / PPV / NPV / LR / ROC）
- 治疗效果评价（RR / ARR / NNT / NNH）
- 预后研究（KM / Cox）
- 系统综述与 Meta 分析（深入）
- EBM 与 GRADE 证据分级
- 公共卫生监测与爆发调查
- 现场流行病学

## 2026-09-09 — 02_Raw/Lectures/ 重组：按学科建立子目录

> 用户反馈：`02_Raw/Lectures/` 下文件越来越多，需要按课程（学科）分类整理。

### 重组前后

**重组前**（扁平结构）：
```
02_Raw/Lectures/
├── 1 绪论.pdf                            （医学微生物学）
├── 1 2 第1章 细菌的形态与结构 1.pdf         （医学微生物学）
├── 第一章 免疫学概述.pdf                      （医学免疫学）
├── 流行病学绪论.pptx                        （临床流行病学）
├── 疾病的分布.pptx                          （临床流行病学）
└── README.md
```

**重组后**（按学科子目录）：
```
02_Raw/Lectures/
├── Medical Immunology/
│   └── 第一章 免疫学概述.pdf
├── Medical Microbiology/
│   ├── 1 绪论.pdf
│   └── 1 2 第1章 细菌的形态与结构 1.pdf
├── Human Parasitology/                    （空目录，待 /ingest）
├── Clinical Epidemiology/
│   ├── 流行病学绪论.pptx
│   └── 疾病的分布.pptx
└── README.md
```

### 操作

- **新建 4 个学科子目录**（与 `03_Concepts/` 中已注册学科一一对应）
- **移动 5 个文件**到对应子目录（保留原始文件名）
- **保留原始文件名**（避免破坏引用 + 保留追溯性）

### 引用更新

- **批量更新 39 个文件**中的 `02_Raw/Lectures/<file>` → `02_Raw/Lectures/<Discipline>/<file>`：
  - 18 个 Clinical Epidemiology Concept 节点
  - 4 个 Immunology Concept 节点
  - 7 个 Medical Microbiology Concept 节点
  - 1 个 Review Session
  - 2 个 Clinical Epidemiology Lectures
  - 1 个 Medical Immunology Lecture
  - 2 个 Medical Microbiology Lectures
  - 3 个 Course 文件（CE / MI / MM）
  - 1 个 Change-Log（保持链接完整性）

### 系统文件

- `02_Raw/Lectures/README.md` 完全重写：
  - 顶部增加"组织结构"说明（与已注册学科一一对应）
  - 各分组更新文件路径
  - 底部增加"文件整理历史"小节

### 未变更

- 原始 PDF / PPTX 文件内容
- `02_Raw/Textbooks/` 目录（已有自己的学科子目录）
- `03_Concepts/`、`04_Clinical/`、`05_Study/` 内容（仅引用路径更新）

### 设计原则

- **学科目录与 03_Concepts/ 一致**：确保原始资料与正式知识按同一坐标系组织
- **保留原始文件名**：避免破坏引用追溯；命名格式 `<序号> <章节名>`
- **人类寄生虫学保留空目录**：待 /ingest 后填充

## 2026-09-09 — PPT→PDF 自动转换 + 保留原文件

> 用户反馈：当讲座原始文件为 PPT/PPTX 时，自动转换为 PDF 并保留原文件。

### 转换工具

- **使用**：Python `win32com.client` + Microsoft PowerPoint COM 自动化
- **方法**：调用 `Presentations.SaveAs(path, 32)`，其中 `32 = ppSaveAsPDF`
- **前提**：本地需安装 Microsoft PowerPoint（本机已安装 Office 16）

### 操作

- **新建**：`02_Raw/Lectures/Clinical Epidemiology/流行病学绪论.pdf`（4.0 MB，由 .pptx 4.4 MB 转换）
- **新建**：`02_Raw/Lectures/Clinical Epidemiology/疾病的分布.pdf`（3.8 MB，由 .pptx 5.1 MB 转换）
- **保留**：原 PPTX 文件**未删除**（用于编辑源）

### Active 文件引用更新（22 个文件）

| 范围 | 文件数 |
|------|--------|
| `03_Concepts/Clinical Epidemiology/*.md` | 18 |
| `08_Courses/Clinical Epidemiology/Course.md` | 1 |
| `08_Courses/Clinical Epidemiology/Lectures/01,02.md` | 2 |
| `99_System/Change-Log.md` | 1 |
| **合计** | **22** |

所有 `*.pptx` 引用 → 改为 `*.pdf`。

### 系统文件

- `02_Raw/Lectures/README.md` 完全重写：
  - 新增 **"文件格式转换规则"** 章节（PDF 首选 / PPTX 保留 / COM 脚本）
  - 更新 Clinical Epidemiology 分组（4 文件 = 2 PPTX + 2 PDF）

### 设计原则

- **PDF 为首选引用**：跨平台稳定、可视化好、文件大小通常更小
- **PPTX 保留为源**：可编辑、保留原始结构
- **统一引用规范**：Active 文件统一指向 PDF，PPTX 仅作源

### 待 /ingest 规则更新

- 未来 /ingest 任何 PPT/PPTX 文件时，自动执行转换 + 保留
- 建议将转换逻辑写入 `99_System/` 下的 SOP 文档（如 `PPT-to-PDF-SOP.md`）
