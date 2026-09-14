---
type: system
status: active
tags:
  - system/log
---

# Change Log — 变更记录

记录 Medicine-Lib 的重大结构变化。

## 2026-09-14 — 规范 /ingest 流程：课件来源必须同步创建课程层 Lecture

> 用户要求：「规范 ingest 流程：ingest 课件时请同步创建 08_Courses 下各科目 lecture 中的相应章节。」

### 背景

病理学第二章 `/ingest` 时，`Ingest-SOP` §3.1 第 4 项写作"课程上下文层（**若需要**）"。
该措辞使 Lecture 看起来是可选项，结果 `08_Courses/Pathology/Lectures/02 损伤的修复.md` 未被创建，
直到用户复核时才发现并单独补齐（见本日 `/ingest 病理学 第二章` 条目末的"用户复核反馈"）。
**根因是流程措辞留了后门，不是执行疏忽** —— 因此本次直接改流程。

### 变更：把"可选"改为"强制"

#### `99_System/Ingest-SOP.md`（274 → 340 行）

- **新增 §3.5「课程上下文层同步（强制 — 课件来源必做）」**，含 6 个子节：
  - §3.5.1 判定表：`S-LEC-*` 强制建 Lecture；`S-TXT-*` / `S-GDL-*` / `S-PAP-*` **不建**
  - §3.5.2 必产三件套：`Course.md`（无则新建）· `Lectures/<NN> <章节名>.md` · 回写 Course 清单与计数
  - §3.5.3 命名规范：`<两位数章节号> <中文章节名>.md`；`chapter:` 用阿拉伯数字
  - §3.5.4 Lecture 必含部分（8 项，缺一即后验不通过）
  - §3.5.5 双向链接：Lecture → MOC，且 **MOC → Lecture**
  - §3.5.6 例外：同章二次 ingest 更新不新建；无 Course 时先建 Course 避免孤儿
- **§0** 新增"课件来源的完整产出清单"7 项，**缺一即视为本次 `/ingest` 未完成**
- **§1.2** 现状调查新增"枚举课程上下文层 `08_Courses/<Discipline>/`"
- **§3.1** 第 4 项由"课程上下文层（若需要）"改为"**课程上下文层同步（课件来源强制）**"，并补"顺序不可颠倒"说明
- **§5.1** 新增必检项 **5.1.7 课程上下文层已同步**（未通过 = 不得交付）
- **§6.1** 主代理职责新增预创课程上下文层（Course + Lecture）
- **§7** 陷阱表新增 3 行：Lecture 漏建 · Lecture 与 MOC 命名不一致 · `章节目标` 伪装成来源
- **§8** 使用示例 Create 步骤新增第 4 步：同步课程上下文层
- **§9** 参考新增 Lecture 模板与 `08_Courses` 职责边界入口

#### `AGENTS.md` §19

- 流程图新增 `Sync Course Layer` 步骤（位于 Add Links 与 Record Sources 之间）
- 新增"课件来源强制产出"段落：必须同批创建 Course + Lecture，缺此项视为 `/ingest` **未完成**；教材 / 指南 / 文献不建 Lecture
- SOP 引用说明补入「课程上下文层同步 §3.5」

#### `08_Courses/README.md`

- 使用规则新增第 5 条：Lecture 由 `/ingest` 同步创建（2026-09-14 起强制），并记录起因

#### `99_System/Templates/17_Lecture.md`

- 模板重写以对齐 §3.5.4 必含部分：补 `course` / `chapter` / `topics` · 来源 callout ·
  `## 章节目标`（含 §26 inference 标注要求）· 各节"详见 MOC"链接 · `Class Notes` 三个 callout ·
  `Related Medical Knowledge` / `Related Questions`，文末附检查清单

### 生效范围与验证

- 自本次起，**所有课件来源的 `/ingest`** 都必须同批产出课程层 Lecture
- 下一章（第三章 局部血液循环障碍）将按新流程执行，作为**首个验证案例**
- 本次未回改历史：病理学第一章、第二章的 Lecture 均已存在，无需补建

## 2026-09-14 — /ingest 病理学 第二章 损伤的修复（S-LEC-012）

> 用户指令：`/ingest 病理学 修复`。严格按 [[Ingest-SOP]] 执行（预检 → 概念提取 → 创建 → 来源登记 → 后验）。

### 预检（Pre-flight）

- 原始资料：`02_Raw/Lectures/Pathology/笔记—修复.docx`（25,044 bytes；163 段落，非空 161）
- 枚举 `03_Concepts/Pathology/` → 22 个预存节点，**全部属第一章**，第二章无重叠 → 无覆盖风险
- Source-Registry 最大号 `S-LEC-011` → 本次登记 `S-LEC-012`

### Concept 层

- **新建第二章 MOC**：`03_Concepts/Pathology/Chapter 2 - Repair.md`
  - aliases：`第二章` / `损伤的修复` / `Chapter 2`
  - **刻意不设 `Repair` 别名** —— `Repair` 已是同名概念节点，避免 wikilink 歧义
- **新建 26 个概念节点**：

| 分组 | 节点数 | 节点 |
|------|--------|------|
| 总论与再生基础 | 7 | Repair · Regeneration · Cell Cycle · Stem Cell · Labile Cells · Stable Cells · Permanent Cells |
| 组织再生机制 | 6 | Epithelial Regeneration · Fibrous Tissue Regeneration · Cartilage Regeneration · Angiogenesis · Muscle Regeneration · Nerve Regeneration |
| 再生影响因素 | 3 | Extracellular Matrix · Growth Factor · Chalone and Contact Inhibition |
| 纤维性修复 | 3 | Fibrous Repair · Granulation Tissue · Scar Tissue |
| 创伤愈合 | 5 | Wound Healing · Healing by First Intention · Healing by Second Intention · Fracture Healing · Factors Affecting Wound Healing |
| 特定病变 | 2 | Traumatic Neuroma · Keloid |

### 课程上下文层

- 新建 Lecture：`08_Courses/Pathology/Lectures/02 损伤的修复.md`
- 更新 Course：`08_Courses/Pathology/Course.md`（Lecture 清单 + 节点分布表 21 → 48）

### System 层

- `99_System/Source-Registry.md` — 追加 `S-LEC-012`（讲座表共 12 行）
- `99_System/Knowledge-Status.md` — 活跃节点 74 → **100**；讲座来源 11 → 12
- `00_Dashboard/Home.md` — 节点 74 → 100；`Pathology` 22 → 48；新增第二章 MOC 入口；Knowledge Gaps 表更新
- `03_Concepts/Pathology/README.md` — 已建节点 22 → 48；待建清单移除第二章、新增"第二章遗留"

### 并行协作（Ingest-SOP §6）

- 主代理：预创 MOC、Source-Registry、Course / Lecture、README、Dashboard、Knowledge-Status，并执行 §5 后验
- 3 个 subagent 并行写入 26 个节点（8 / 9 / 9，写集互不重叠）
- subagent **未触碰** MOC / README / Source-Registry / Change-Log / 原始资料

### 后验结果（SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 路径解析 | 28 个新文件中 408 条 wikilink；**真断链 0**（13 条未解析均为刻意保留的待建节点 + MOC 中的原始 `.docx` 附件链接） |
| 5.1.2 变位字扫描 | **0 命中**（SOP 禁用字表 + 已知错字表双重扫描） |
| 5.1.3 frontmatter 一致性 | 26 个节点**共用 1 种字段签名**，问题 0 |
| 5.1.4 段落号引用 | 26 个节点全部带 `paragraphs NNN–NNN`，可回溯讲义原文 |
| 5.1.5 Source-Registry | `S-LEC-012` 在表内；共 12 行；无乱码 / `??` |
| 额外 | ASCII 字母与中文相邻：0；BOM：0；缺尾换行：0 |

### 后验发现并修正

- **`Growth Factor.md`**：subagent 曾补入 7 个因子的中文全称（如"血小板源生长因子"），但**讲义原文仅给出缩写** → 已改为只列缩写 + 加 `讲义未详述` 警示（依 AGENTS.md §32「Prefer sources over memory」）
- **`Stem Cell.md`**：帕金森病 / 阿尔茨海默病 / 糖尿病 / 心肌梗死 原为纯文本 → 改为待建 wikilink，与 MOC 的待建清单及第一章"链接优先"惯例一致
- **讲义结构说明**：讲义**仅"第一节 再生"有显式节标题**，"纤维性修复""创伤愈合"两部分无节标题 → MOC 与 Lecture 均显式标注划分依据为原文编号，**未伪造节标题**
- **用户复核反馈（补齐 Lecture 章节目标）**：Lecture `02 损伤的修复.md` 原缺 Lecture 01 具备的 `## 章节目标` 小节 → 已补齐，依讲义实际篇幅推断 掌握 / 熟悉 / 了解 三层，并**显式标注为 inference**（讲义原文未标注掌握程度）；同时为 Lecture 01 原有同类表格补加相同 inference 标注（AGENTS.md §26）

### 安全网

- 26 个节点均 `type: pathophysiology|physiology` · `evidence_level: C` · `source_status: needs_review` · `last_reviewed: 2026-09-14`
- 讲义未覆盖处显式标注 `讲义未详述`（如生长因子未给功能、瘢痕疙瘩未给临床处理）
- 原始 `.docx` 未修改；第一章 22 个节点与 MOC 未修改

### 待 /ingest 后续章节

- 第三章 局部血液循环障碍 · 第四章 炎症 · 第五章 肿瘤 · 第六章 免疫病理 · 第七~十八章 各论

## 2026-09-14 — 一致性修复（bug fix pass）：BOM / 断链 / 文档漂移 / 教材登记

> 用户指令：「修复 bug」。修复 2026-09-14 工作区结构分析中确认的 5 类缺陷。**未修改任何医学事实**（定义 / 机制 / 剂量 / 数值）。

### 修复 1 — UTF-8 BOM 破坏 frontmatter 解析（42 个文件）

- **问题**：42 个 `.md` 文件以 UTF-8 BOM（`EF BB BF`）开头、位于 `---` 之前，使 Obsidian 属性面板与 YAML 解析器无法识别 frontmatter
- **修复**：逐字节剥离 BOM；不触碰其他任何字节，各文件原有 CRLF/LF 行尾保持不变
- **效果**：无 frontmatter 的 `.md` 文件 **44 → 2**（余 `AGENTS.md`、`99_System/Archive/Concepts-Retired.md`，二者本不需要）
- **范围**：8 个活跃文件（`03_Concepts/Pathology/{README,Hyperplasia,Hypertrophy,Metaplasia}.md`、`03_Concepts/Diseases/Diabetes Insipidus.md`、`07_MOCs/Nephrology MOC.md`、`99_System/Source-Registry.md`、`02_Raw/Lectures/Pathology/README.md`）+ 34 个存档文件

### 修复 2 — 断链：免疫学节点指向不存在的原始文件（27 处 / 14 文件）

- **问题**：`[[02_Raw/Lectures/Medical Immunology/第三章 抗原(1).pdf]]` —— 实际文件名为 `第三章 抗原.pdf`（PPT→PDF 转换改名遗留）
- **修复**：27 处全部改为实际文件名，含 12 个 Immunology 概念节点 ×2（正文引用 + Sources）、`08_Courses/Medical Immunology/Lectures/03 抗原.md`、本 Change-Log
- **效果**：含未解析链接的文件 **46 → 36**，"指向不存在文件"这一类缺陷清零
- 另有 1 处路径笔误：本日志 2026-09-11 `/setup` 条目中 `[[02_Raw/Lectures/Pathology/Pathology|Pathology 课程]]` → 修正为 `[[08_Courses/Pathology/Course|Pathology 课程]]`

### 修复 3 — AGENTS.md §4 已注册学科清单滞后

- **问题**：清单只列 4 个学科，节点数陈旧（Immunology 4 / Human Parasitology 0 / Clinical Epidemiology 0，均为"待 /ingest"），且**遗漏第 5 个注册学科 Pathology**
- **修复**：`AGENTS.md` §4 更新为 5 个学科实名 + 当前节点数（16 / 7 / 11 / 17 / 22），并注明"节点数为概念节点，不含 README 与 MOC"

### 修复 4 — 文档计数与结构漂移

| 文件 | 原值 | 更正 |
|------|------|------|
| `03_Concepts/Pathology/README.md` | 已建节点 21 · 新建 21 个概念节点 | **22**（两处） |
| `07_MOCs/Medicine MOC.md` | Pathology 21 节点；"核心知识入口"漏列 Pathology | **22** + 补列 |
| `00_Dashboard/Home.md` | 学习材料行仍写"27 道题…Flashcards/Wrong-Answers/Review 仍空"；原始资料"11 份"；退役存档"40 节点" | 15 题 / 10 卡 / 1 复习 / 0 错题；12 份原始课件 + 11 个讲座来源；**38 概念节点**（+2 原 README） |
| `99_System/README.md` | Templates（15 个）；目录树缺 `08_Courses`；文件清单缺 Ingest-SOP | **20 个** + 补 `08_Courses` + 补 Ingest-SOP / Archive |
| `99_System/Knowledge-Status.md` | "活跃概念节点 73（1 Disease · 16 · … · 22）"口径自相矛盾 | **74 = 学科节点 73 + 跨学科目录 1**；补教材登记状态；`last_updated` → 2026-09-14 |
| `99_System/Source-Registry.md` | `S-LEC-011` 行与表体之间夹空行，脱离表格 | 并入讲座表 |

### 修复 5 — 教材登记补全（`Textbook-Import-SOP` 步骤 ⑥⑦）

- **问题**：`02_Raw/Textbooks/` 已有 4 份 PDF，但 Source-Registry 教材区为空；仅 Pathology 有子目录 README
- **新建 3 份 README**：`Medical Microbiology` / `Clinical Epidemiology` / `Medical Immunology`
- **追加登记**：`S-TXT-001` ~ `S-TXT-004`（均 `reference-only / not-ingested`）
- **补齐 Pathology README 元信息**：原写"出版年份未知、ISBN 待补充"，实际 PDF p3 版权页**可提取** → 2024 年 7 月第 10 版、ISBN 978-7-117-36468-3、人民卫生出版社、副主编名单
- ⚠️ **重要发现（影响 `needs_review` 核对计划）**：
  - `流行病学9版教材.pdf`（364 页）为**纯图像扫描版** —— 全部 364 页仅含 12 字符水印「微信公众号：公卫人小分队」，**无文本层**
  - `免疫系统与疾病.pdf`（338 页）为**纯图像扫描版** —— 全部页面文本 0 字符
  - ⇒ 这两份教材**在 OCR 前不可用于逐句核对**
  - `11.医学微生物学.pdf`（386 页）与 `《病理学（第10版）》.pdf`（418 页）**有文本层，可用于核对**

### 安全网 / 未变更

- 未修改任何医学事实；`03_Concepts/` 内的改动仅限于链接目标修正（12 个 Immunology 节点）、计数修正（Pathology README）与 frontmatter 前导 BOM 剥离
- 未删除任何文件；未改动 `02_Raw/` 下的原始 PDF / DOCX
- 修复脚本与扫描报告位于 `temp/`（已被 `.gitignore` 排除）：`structure_analysis.py`、`bugfix_pass1.py`、`bugfix_pass2.py`、`textbook_scan.py`、`textbook_verify.py`

### 遗留（仅报告，未修复）

- 5 个文件存在**行尾混用**（各含 1 处 CRLF，其余 LF）：`03_Concepts/Pathology/{Hyperplasia,Hypertrophy,Metaplasia}.md`、`05_Study/Flashcards/FC-Imm-06-Neutrophil-KeyData.md`、`FC-Imm-08-TCR-BCR-Receptors.md` —— 不影响解析，未改动以遵守 §27
- `02_Raw/Textbooks/Human Parasitology/` 为空目录（无教材文件）
- `.gitignore` 忽略整个 `02_Raw/`（仅 `02_Raw/Lectures/` 例外），故 4 份教材 README 与登记信息**不进版本库** —— 需人工决定是否放行 `!02_Raw/**/README.md`
- 本日志 2026-09-08 条目中 `[[03_Concepts/Infectious Disease|Infectious Disease]]` 指向已拆分删除的学科目录；属历史记录，保留不改
- 其余 36 个文件的未解析链接均为"先链接、后建节点"的**待建概念**（Knowledge Gaps）、SOP/模板占位符或存档内部链接，非缺陷

## 2026-09-11 — 注册新学科：病理学（Pathology）与首个 /ingest

> 用户反馈：注册“病理学”作为第 5 个已注册学科，同时对第一章“组织细胞适应与损伤”执行 /ingest。

### 操作

#### Concept 层

- **新建学科目录**：`03_Concepts/Pathology/`
- **新建 README**：`03_Concepts/Pathology/README.md`（包含学科范围、已建/待建节点、使用规则）
- **新建第一章 MOC**：`03_Concepts/Pathology/Chapter 1 - Cellular Adaptation and Injury.md`（适应 + 可逆损伤 + 细胞死亡 三大板块导航）
- **新建 21 个概念节点**（均 `type: pathophysiology`）：

| 节点 | type | 要点 |
|----------|------|----------|
| [[Atrophy]] | pathophysiology | 萎缩（6 种病理性类型 + 质量变化） |
| [[Hypertrophy]] | pathophysiology | 肥大（代偿性与内分泌性） |
| [[Hyperplasia]] | pathophysiology | 增生（分裂能力与组织对应） |
| [[Metaplasia]] | pathophysiology | 化生（上皮与间叶） |
| [[Cellular Aging]] | pathophysiology | 细胞老化 |
| [[Cell Injury]] | pathophysiology | 损伤原因（8 类）与机制 |
| [[Cellular Swelling]] | pathophysiology | 细胞水肿 / 水变性 |
| [[Fatty Change]] | pathophysiology | 脂肪变（胝斑心、脂肪脑） |
| [[Hyaline Degeneration]] | pathophysiology | 玻璃样变（3 型） |
| [[Amyloidosis]] | pathophysiology | 淀粉样变 |
| [[Mucoid Degeneration]] | pathophysiology | 黏液样变 |
| [[Pathologic Pigmentation]] | pathophysiology | 四种色素：含铁血黄素 / 脂褐素 / 黑色素 / 胆红素 |
| [[Pathologic Calcification]] | pathophysiology | 营养不良性 / 转移性钙化 |
| [[Cell Death]] | pathophysiology | 细胞死亡总论 |
| [[Necrosis]] | pathophysiology | 坏死总论 + 组织学变化 |
| [[Coagulative Necrosis]] | pathophysiology | 凝固性坏死 |
| [[Liquefactive Necrosis]] | pathophysiology | 液化性坏死 |
| [[Caseous Necrosis]] | pathophysiology | 干酪样坏死 |
| [[Fat Necrosis]] | pathophysiology | 脂肪坏死 |
| [[Fibrinoid Necrosis]] | pathophysiology | 纤维蛋白样坏死 |
| [[Gangrene]] | pathophysiology | 坏痁（干/湿/气） |
| [[Apoptosis]] | pathophysiology | 调式（调引与调小体） |

> **节点计数：21 个 pathophysiology + 1 个 MOC（该 MOC 本身不计入 active 节点总数）**

#### System 层

- **新建：** `02_Raw/lectures/Pathology/`（原始讲义目录）与 `02_Raw/lectures/Pathology/README.md`
- **更新：** `99_System/Source-Registry.md` — 追加 `S-LEC-011`：Pathology Chapter 1 — Cellular Adaptation and Injury（优课联盟 UOOC，2026 秋）

### 安全网

- 所有新建节点 `source_status: needs_review`（lecture-derived，待与权威教材逐句核对）
- 原始 `.docx` 未修改；文件名保留（“笔记—组织细胞适应与损伤.docx”）
- Wiki-links 在互联同一章内都能正常解析

### 未变更

- `AGENTS.md` — 未修改（学科注册规则已在 V2 中明确）
- `00_Dashboard/Home.md` — 需后续手动更新学科统计
- `07_MOCs/Medicine MOC.md` — 需后续补充 Pathology 行
- `99_System/Knowledge-Status.md` — 需后续更新节点总数
- `08_Courses/` — 未创建 Pathology Course（仅需要时可占位）

### 待 /ingest 后续章节

- 第二章 损伤的修复
- 第三章 局部血液循环障碍
- 第四章 炎症
- 第五章 肿瘤
- 第六章 免疫病理
- 第七”十八章 各论（各系统疾病）

## 2026-09-11 — /setup 病理学：建立课程上下文层

> 用户反馈：在完成 [[03_Concepts/Pathology|Pathology]] 学科首个 /ingest 后进行 /setup，为 [[08_Courses/Pathology/Course|Pathology 课程]] 建立课程上下文层。

### 操作

#### Course 层

- **新建课程目录**：`08_Courses/Pathology/`
- **新建 Course**：`08_Courses/Pathology/Course.md`
  - course_code: `UOOC-MED-PATHOLOGY-2026`
  - semester: 2026 秋
  - instructor: 优课联盟 UOOC 慕课（线上学习）
  - discipline: Pathology
  - textbook: 人卫版《病理学》（第 9/10 版）
- **新建 Lectures/ 子目录**
- **新建 Lecture**：`08_Courses/Pathology/Lectures/01 组织细胞适应与损伤.md`
  - 类型：lecture（chapter 1）
  - 涻盖：适应 5 种 + 损伤 8 原因机制 + 可逆性变性 7 种 + 细胞死亡 6 亚型 + 调弎
  - 源头：`S-LEC-011`（[[02_Raw/Lectures/Pathology/笔记—组织细胞适应与损伤.docx]]）
  - 并详细链接所有 21 个 [[03_Concepts/Pathology|θ理学学科]] 节点及第一章 MOC
  - 包含 `Class Notes` （源文本特点 / 我的疑问 / AI 补充）

#### 未创建

- **Exams/** 子目录 — 待 review 后补充
- **Reviews/** 子目录 — 待 /study 时创建
- **02–18 章 Lecture** — 待 /ingest 后逐章创建

### 与现有学科的区别

- Pathology 是唯一以 **UOOC 慕课形态** 设立的 Course；其他 Course（Medical Immunology / Microbiology / Parasitology / Epidemiology）为现席课形态，含 `instructor: 具体老师`
- Pathology Course 的 “考核比例” 与 “讲者” 字段使用 UOOC 平台专属说明（6030期末）

### 安全网

- 原始 `.docx` 未修改
- `99_System/Source-Registry.md` `S-LEC-011` 未变更
- `99_System/Knowledge-Status.md` 未变更（课程上下文层不计入 active 节点总数）
- AGENTS.md 未修改

### 待执行

- [ ] /ingest 后续章节时同步创建对应 Lecture
- [ ] /study Pathology 后创建 Exams/ 与 Reviews/ 子目录
- [ ] Pathology Course 与 [[02_Raw/Lectures/Pathology/README]] 双向链接验证

## 2026-09-11 — 制定 /ingest 详细 SOP

> 用户反馈：规范 `/ingest` 作业流程。依据 Pathology · 第一章 /ingest 过程中遇到的问题（预存文件漏检· Unicode 错位· 路径偏移· 并行 agent 覆盖），提炼为可重复使用的检查清单与防护措施。

### 操作

- **新建 SOP**：[[99_System/Ingest-SOP.md|/ingest 作业流程 SOP]]
  - 10 个主章节：三条黄金规则 · 预检 · 概念提取 · 写作 · 源登记 · 后验 · 并行 agent 协作 · 阵阱 · 例 · 参考
  - 主要改进：
    1. **预检阶段给出逐项检查清单**（资料清点 · 现状调查 · 预存节点报告）
    2. **写作阶段明确三个顺序**（MOC · Discipline README 优先 → 子节点 → 跨文件链接）
    3. **Frontmatter 强制模板**（不多不少）
    4. **写作安全规则表**（Unicode 转义 · 中英混排 · 同字似字 · 路径偏移 · 错位代号）
    5. **优先纯基名引用**（避免路径跟足）
    6. **后验流程五项必检**（路径解析 · 错别字扫描 · Frontmatter 一致性 · Source-Registry 中文验证 · Change-Log 入库）
    7. **并行 / 多 Agent 协作模式**（主代理 · Subagent 职责划分）
    8. **阵阱表**（以本次遇到的具体例子记录）

- **修改 AGENTS.md**：§ 19 “/ingest” 末尾增加引用指向 [[99_System/Ingest-SOP.md|Ingest-SOP]]（明确“本节仅作高层概述·详细 SOP 在另一处”）

### 背景：为什么需要这份 SOP？

本次 /ingest 病理学 · 第一章遇到以下问题：

1. **预存文件漏检**：Pathology/ 目录里有 6 个上一轮创建的节点，但主代理初次枚举只看到 README 与 MOC，使 subagent 产生了“预存文件”的错觉。
2. **Unicode 错位**：使用 `\u82ac` 等转义时出现 东 (冬)/弎/豹 · 需 unicodedata 验证。
3. **路径偏移**：49 个 wiki-link 用了 `../../` 但实际需 `../../../` · 后验中发现。
4. **多 Agent 覆盖**：3 个 subagent 并行写入同一目录· Hooke 将 Pauli 刚刚创建的 6 个文件当作“预存”。

### 未变更

- AGENTS.md 其他节（§20-32）未变动
- 99_System/Textbook-Import-SOP.md 未变动（都是参考资源）
- 99_System/Templates/ 未变动

### 待执行

- [ ] 后续 /ingest · ···时跟 SOP 检查清单实施、主动报告
- [ ] 同步修改 · 完善 /setup · /study /quiz /case 的类似检查清单
- [ ] 考虑给 /connect /audit /quiz 也增加 SOP 文件
## 2026-09-11 — 全面扫描与状态同步

> 用户反馈：扫描知识库并同步状态文件。以 [[99_System/Ingest-SOP.md|Ingest-SOP]] 5.1 后验为准，重新扫描 281 个 .md 文件，重新令 Dashboard / Knowledge-Status / Change-Log 与实际一致。

### 扫描结果（canonical）

| 指标 | 值 |
|------|------|
| 活跃概念节点 | **74**（1 Disease + 16 Immunology + 7 Medical Microbiology + 17 Clinical Epidemiology + 11 Human Parasitology + 22 Pathology） |
| 已注册学科 | **5** |
| 活跃 Course | **5** |
| Lecture | **8**（2 + 2 + 1 + 2 + 1） |
| 已注册源 S-LEC-* | **11**（S-LEC-001 ~ 011） |
| 模板 | **20** |
| MOC（07_MOCs/） | 16 个（中 1 个为总 MOC） |
| 练习题 | 15 活跃 + 27 退役 |
| 闪卡 | 10 （FC-Imm-01 ~ 10） |
| 复习会话 | 1 |
| 错题 | 0 |
| 退役概念 | **40** 节点（Physics/Pathophysiology 存档） |

### 发现的差异（已修正）

- **Dashboard “知识节点”行：**73 → 74；Pathology 21 → 22
- **Dashboard “退役存档”：**38 → 40
- **Dashboard “Immunology（4 节点）”：**4 → 16
- **Dashboard “Clinical Epidemiology（0 节点，待 /ingest）”：**“0 节点” → 17 节点 + 颚额示例节点（误居在 Epidemiology 下，已移除）
- **Dashboard “Pathology（21 节点）”：**21 → 22
- **Dashboard “Flashcards（0）” / “Review（0）”：**0 → 10 / 0 → 1
- **Dashboard “临床流行疵学 Course”中的错别字：**“疵学”（U+75B5 = 疵）→ “病学”（U+75C5 = 病）
- **Knowledge-Status “活跃节点”：**5 → 74
- **Knowledge-Status “活跃概念节点：73”：**73 → 74；Pathology 21 → 22
- **Knowledge-Status “S-LEC-001 ~ 006”：**→ S-LEC-001 ~ 011（原描迹出 S-LEC-007 ~ 011）
- **Knowledge-Status “全部 5 节点 source_status”：**5 → 74（所有节点 均 为 lecture-derived）

### 未变更

- 02_Raw/ · 03_Concepts/ · 04_Clinical/ · 05_Study/ · 06_Specialties/ · 07_MOCs/ · 08_Courses/ 原始文件未修改
- 99_System/Source-Registry.md 未变动（仅检查中文是否受损）
- 99_System/Ingest-SOP.md 未变动
- AGENTS.md 未变动

### 下次扫描建议

本次手工扫描 + 修正，下次建议改为脚本化（`99_System/scripts/scan.py`），运行后生成同步报告。

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

## 2026-09-09 — /ingest 人体寄生虫学 总论

> 用户对刚注册的 `[[03_Concepts/Human Parasitology|Human Parasitology]]` 学科执行首次 /ingest。原始资料：`02_Raw/Lectures/Human Parasitology/第一讲 寄生虫学总论2026秋 28号字(1).ppt`（旧版 PPT 格式，6.1 MB），讲者申成华（病原生物学教研室）。

### 工具确认 + PPT→PDF 转换

- **旧版 .ppt 格式**：python-pptx 不支持，仅支持 .pptx
- 通过 **Microsoft PowerPoint COM 自动化** 处理 → 生成 PDF（2.5 MB）
- 保留原 .pt 文件供编辑（按 PPT→PDF 规则）

### 注册讲座来源

- `S-LEC-009` — 《第一讲 寄生虫学总论》（申成华，2026 秋）

### Created（Course / Lecture 层）

- `[[08_Courses/Human Parasitology/Course|Human Parasitology Course]]`（更新：从空 → 含 1 个 Lecture）
- `[[08_Courses/Human Parasitology/Lectures/01 寄生虫学总论|01 寄生虫学总论 Lecture]]`

### Created（Concept 层 — 11 个节点，全部放在 `03_Concepts/Human Parasitology/`）

| 节点 | 核心内容 |
|------|----------|
| [[Parasitology]] | 学科定义、范畴（蠕虫/原虫/节肢动物）、在医学中的位置 |
| [[Medical Helminthology]] | 蠕虫分类（吸虫/绦虫/线虫/棘头虫） |
| [[Medical Protozoology]] | 原虫（疟原虫/阿米巴/弓形虫/隐孢子虫/肺孢子虫） |
| [[Medical Arthropodology]] | 节肢动物（蚊/蚤/虱/蜱螨）作为传播媒介 |
| [[Symbiosis Types]] | 三种共生类型（片利/互利/寄生）+ 寄生演化方向 |
| [[Parasite Life Cycle]] | 直接型 vs 间接型 + 感染期 + 世代交替 |
| [[Parasite-Host Classification]] | 寄生虫分类（部位/时间/宿主选择/免疫）+ 宿主分类（终/中/保虫/转续） |
| [[Parasitic Zoonoses]] | WHO TDR 10 大热带病 + 新现/再现/动物源性寄生虫病 |
| [[Parasitic Infection Characteristics]] | 5 大临床特点（慢性/隐性/多寄生/异位/幼虫移行）+ 致病机制 |
| [[Parasitic Disease Epidemiology]] | 3 个环节 + 7 类传播途径 + 3 类影响因素 + 流行特点 |
| [[Parasitic Disease Prevention]] | 3 大环节阻断 + 我国防控成果（血吸虫 79.9万 / 疟疾 2021 消灭 / 丝虫 1994 消灭 / 黑热病 1958 消灭）|

### Updated

- `[[99_System/Source-Registry|Source-Registry]]` — 追加 S-LEC-009
- `[[02_Raw/Lectures/Human Parasitology/]]` — 新建 PDF（2.5 MB）
- `[[03_Concepts/Human Parasitology/README|README]]` — 已建节点清单更新
- `[[08_Courses/Human Parasitology/Course|Course]]` — Lectures 列表添加
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 节点统计（12 → 23）

### 未变更

- `02_Raw/Lectures/Human Parasitology/第一讲 寄生虫学总论...ppt`（保留）
- AGENTS.md（已正确列出 Human Parasitology 为注册学科 3）

### 待 /ingest 后续章节

- 线虫概论及线虫各论（6h）
- 吸虫概论及各论（4h）
- 绦虫概论及各论（4h）
- 医学原虫学各论（5h）
- 医学节肢动物学各论（1h）

## 2026-09-09 — /ingest 免疫学 抗原（Chapter 3）

> 用户对 `[[03_Concepts/Immunology|Immunology]]` 学科执行第 2 次 /ingest（第 1 次为 2026-09-07 免疫学概述）。原始资料：`02_Raw/Lectures/Medical Immunology/第三章 抗原.pdf`（56 页），讲者杨艳艳（基础医学院免疫学系）。

### 注册讲座来源

- `S-LEC-010` — 《第 3 章 抗原》（杨艳艳，2026 秋）

### Created（Course / Lecture 层）

- `[[08_Courses/Medical Immunology/Course|Medical Immunology Course]]`（更新：加入 Lecture 03）
- `[[08_Courses/Medical Immunology/Lectures/03 抗原|03 抗原 Lecture]]`

### Created（Concept 层 — 12 个节点，全部放在 `03_Concepts/Immunology/`）

| 节点 | 核心内容 |
|------|----------|
| [[Antigen]] | 抗原定义 + 两大特性（免疫原性 + 免疫反应性） |
| [[Complete Antigen vs Hapten]] | 完全抗原 vs 半抗原 + 半抗原-载体效应 |
| [[Epitope]] | 抗原表位（线性 vs 构象）+ 抗原结合价 |
| [[T Cell Epitope vs B Cell Epitope]] | T 表位（线性、MHC 必需） vs B 表位（构象为主、表面、无 MHC） |
| [[Cross-Reaction]] | 共同抗原表位 + 交叉反应（链球菌-心脏交叉为例）|
| [[Immunogenicity Factors]] | 7 大抗原自身因素 + 宿主因素 + 接种途径 |
| [[TD-Ag vs TI-Ag]] | 胸腺依赖性 vs 非依赖性抗原（结构 + 抗体 + 免疫记忆对比）|
| [[Antigen Classification by Origin]] | 异嗜性 / 异种 / 同种异型 / 自身 / 独特型抗原 |
| [[Endogenous vs Exogenous Antigen]] | 内源性（MHC I/CD8⁺） vs 外源性（MHC II/CD4⁺）|
| [[Superantigen]] | 超抗原：非特异性激活 2–20% T 细胞 → 中毒性休克 |
| [[Adjuvant]] | 佐剂：氢氧化铝 / MF59 / AS04 / VLP / 弗氏等 |
| [[Mitogen]] | 丝裂原：PHA、ConA、LPS、PWM + 淋巴细胞转化实验 |

### Updated

- `[[99_System/Source-Registry|Source-Registry]]` — 追加 S-LEC-010
- `[[08_Courses/Medical Immunology/Course|Course]]` — Lectures 列表 + Source 列表同步
- `[[99_System/Knowledge-Status|Knowledge-Status]]` — 节点统计（40 → 52）

### 未变更

- `02_Raw/Lectures/Medical Immunology/第三章 抗原.pdf` — 未修改
- AGENTS.md（已正确列出 Immunology 为注册学科 1）

### 教学要点（来自 Lecture 03）

- **抗原两大特性**：免疫原性（被 TCR/BCR 识别+激活） + 免疫反应性（与效应产物结合）
- **完全抗原 vs 半抗原**：半抗原 = 只有免疫反应性；与载体交联后获得免疫原性
- **表位是关键**：T 表位（线性、MHC 必需）vs B 表位（构象为主、表面、无需 MHC）
- **TD-Ag vs TI-Ag**：免疫记忆是关键差异 → 影响疫苗设计
- **按亲缘分类**：异嗜性 / 异种 / 同种异型（HLA）/ 自身 / 独特型
- **内/外源性抗原**：MHC I（CD8⁺） vs MHC II（CD4⁺）
- **超抗原**：非特异性激活 2–20% T 细胞 → 中毒性休克
- **佐剂机制**：延缓降解、促进摄取、激活 APC、调节应答类型
- **接种途径**：皮内 > 皮下 > 肌内 > 腹腔 > 静脉

### 课堂测试题（已记录在 Lecture 文件）

9 道 PPT 测试题（p47-55）：
- Q-Imm-16（半抗原多选）
- Q-Imm-17（抗原特异性决定基础）
- Q-Imm-18（B 细胞表位错误选项）
- Q-Imm-19（最强免疫原性物质）
- Q-Imm-20（免疫原性因素错误项）
- Q-Imm-21（最强免疫途径）
- Q-Imm-22（ABO 血型抗原分类）
- Q-Imm-23（超抗原特性）
- Q-Imm-24（佐剂错误描述）

### 待 /ingest 后续章节

- 第 4 章：免疫器官与组织
- 第 5 章：抗体（免疫球蛋白）
- 第 6 章：补体系统
- 第 7-8 章：T/B 淋巴细胞
- 第 9 章：细胞因子
- 第 10 章：MHC / HLA
- 第 11 章：抗原递呈
- ...

## 2026-09-09 — 02_Raw/Textbooks/ 重组：按学科建立子目录

> 用户反馈：`02_Raw/Textbooks/` 下文件散落，需要按学科分类整理。延续 02_Raw/Lectures/ 已有的按学科子目录组织方式。

### 重组前后

**重组前**（散落 + 1 个子目录）：

```
02_Raw/Textbooks/
├── 11.医学微生物学.pdf                    ← 散落
├── 免疫系统与疾病.pdf                       ← 散落
├── 流行病学9版教材.pdf                      ← 散落
├── README.md
└── Pathology/                              ← 已有
    ├── README.md
    └── 《病理学（第10版）》.pdf
```

**重组后**（按学科子目录，与 03_Concepts/ 注册学科一一对应）：

```
02_Raw/Textbooks/
├── Medical Microbiology/                  ← 注册学科 2
│   └── 11.医学微生物学.pdf
├── Medical Immunology/                    ← 注册学科 1
│   └── 免疫系统与疾病.pdf
├── Human Parasitology/                    ← 注册学科 3（空，待补充）
├── Clinical Epidemiology/                 ← 注册学科 4
│   └── 流行病学9版教材.pdf
├── Pathology/                             ← 病理学（未注册学科）
│   ├── README.md
│   └── 《病理学（第10版）》.pdf
└── README.md
```

### 操作

- **新建 4 个学科子目录**（与 `03_Concepts/` 已注册学科一一对应）：
  - `Medical Microbiology/`
  - `Medical Immunology/`
  - `Human Parasitology/`（空，预留）
  - `Clinical Epidemiology/`
- **移动 3 个散落文件**到对应子目录（保留原始文件名）
- **保留** `Pathology/` 既有结构与 `README.md`（已注册为 Reference Source）

### 关联更新

- `02_Raw/Textbooks/README.md` 完全重写：
  - 顶部增加 "组织结构" 图示（5 个学科子目录）
  - 各分组更新文件路径 + 状态标注
  - 新增 "待办"：3 本新教材待注册 Reference Source
- `02_Raw/README.md`（顶层）— 标注 Textbooks + Lectures 已按学科子目录组织

### 设计原则

- **学科目录与 03_Concepts/ 一致**：未来注册新学科时同步建立对应 Textbooks 子目录
- **保留原始文件名**：避免破坏引用追溯
- **Pathology 子目录保留**：已注册的 Reference Source 文档不被破坏

### 待办（不影响当前物理整理）

- 为 3 本新教材（医学微生物学 / 免疫系统与疾病 / 流行病学 9 版）按 `[[99_System/Textbook-Import-SOP|SOP]]` 建立 Reference Source README（包含元信息、完整性检查记录）
- 提供人体寄生虫学教材
- 是否将基础学科（循环 / 泌尿 / 消化）作为新学科注册？
