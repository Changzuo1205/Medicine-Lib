---
type: system
status: active
tags:
  - system/log
---

# Change Log — 变更记录

记录 Medicine-Lib 的重大结构变化。

## 2026-09-23 — /ingest 医学免疫学 第五章 补体系统

> 用户要求：「/ingest 免疫学 补体系统」。

### 来源

`02_Raw/Lectures/Medical Immunology/第五章 补体系统.pdf`（58 页 PPT，杨艳艳，基础医学院免疫学系，2026 秋）→ 登记为 **S-LEC-018**。
课程层编号沿用「章号 = 编号」口径，本讲为 **`05 补体系统`**（第二章仍未摄入，编号无 02）。

### Created：15 个概念节点（医学免疫学 31 → 46；全库 178 → 193）

| 组 | 节点 | type | 来源页 |
|----|------|------|--------|
| 概述（2） | `Complement System` · `Complement Components` | physiology | p4–p10 |
| 激活（5） | `Complement Activation` · `Classical Pathway` · `Alternative Pathway` · `Lectin Pathway` · `Membrane Attack Complex` | physiology | p13–p33 |
| 调节（1） | `Complement Regulation` | physiology | p35–p40 |
| 生物学意义（5） | `Complement-Dependent Cytotoxicity` · `Opsonization` · `Anaphylatoxin and Chemotaxis` · `Immune Adherence` · `Complement Pathophysiological Significance` | physiology | p43–p48、p53 |
| 与疾病（2） | `Complement Deficiency` · `Complement and Infection` | **pathophysiology** | p50–p51 |

### Updated

- **新建 `08_Courses/Medical Immunology/Lectures/05 补体系统.md`**：含 Lecture Overview / 章节目标 / 章节结构 / 五节正文 / **课堂测试题** / Class Notes / Related Medical Knowledge（15 节点 + 跨章）/ Related Questions；正文 `详见 [[Node]]。` 16 处
- **`08_Courses/Medical Immunology/Course.md`**：Lectures 清单追加第 5 讲；`Related Medical Knowledge` 由 31 扩为 **46 节点**；`Knowledge Gaps` 已摄入章节补第五章；`Source` 段补第五章 PPT 与 `S-LEC-018`
- **`03_Concepts/Immunology/README.md`**：节点清单 `31` → **`46`**，新增「第五章 · 补体系统」分组（按概述/激活/调节/生物学意义/与疾病分列）；「待建节点」中删除已建的 `Complement（补体）`；「未摄入章节」说明补第五章
- **`99_System/Source-Registry.md`**：新增 `S-LEC-018`
- **计数回写**：`AGENTS.md` §4（31 → 46）、`00_Dashboard/Home.md`（178 → **193 节点**；免疫学 31 → 46）、`99_System/Knowledge-Status.md`（178 → 193）

### 本讲特点：章节目标**来源直接给出**（第三次），且讲义自带 8 道测试题

- 讲义 p3「重点难点」明确标注三层（掌握：三条激活途径及生物学功能；熟悉：组成及调控因素；了解：成分与调控异常和相关疾病），p57 另有「本章要点」三条（三条途径区别 / 生物功能 / **Complement、MAC 概念**）→ `## 章节目标` **直接引用原文**，未用 inference 标注
- 讲义 p11–p54 嵌入 **8 道自测题** → 按本学科既有做法在 Lecture 内新增 **`## 课堂测试题` 块**（题干 + 选项，正确答案加粗），编号 **Q-Imm-25~32**

### 顺带修复：`03 抗原` Lecture 的一处**不成立的声明**

`08_Courses/Medical Immunology/Lectures/03 抗原.md` 的课堂测试题块标题原为「**已转写为正式 Q 节点**」，但其 9 道题（`Q-Imm-16`~`24`）**从未建为独立文件**（已用 glob 逐号核实：`05_Study/Questions/` 下只有 `Q-Imm-01`~`15`）—— 该声明与事实不符。
已改为「**讲义原题，记录于本块**」，与同文件 `## Related Questions` 的「已记录于课堂测试题块」口径一致；并**保留 16–24 号为该块占用**，故本讲补体的题目从 **25** 起编号。
> 待办建议：若希望把这 9 道题并入正式题目体系，应另起 `/quiz` 作业补建 `Q-Imm-16`~`24` 节点（本知识库不在 `/ingest` 中代建）。

### 结构与取舍（不发明医学事实）

- **节点粒度对照讲义实况**：四类生物学功能**各自独立成节点**（CDC / 调理作用 / 过敏毒素与趋化 / 免疫黏附），因为讲义 p43–p46 逐条展开且均为可独立引用的命名概念；而第五节的「**补体与炎症性疾病**」（p53，仅 2 条）**并入** `Complement Pathophysiological Significance`，并在节点内注明该归并**非讲义原结构**
- **`type` 按语义区分**：13 个正常生理/机制节点用 `physiology`；`Complement Deficiency` 与 `Complement and Infection` 讲缺陷与疾病关联，用 `pathophysiology` —— 与本学科既有的 `Immune Dysregulation`（pathophysiology）口径一致
- **讲义排版错乱处如实标注、不代为重构**：① p33 三条途径比较表中 **MBL 途径的「参与成分」格缺失**，C5-9/B/D/P 因子归属在文本层重复；② p20 写 MAC 致「**胞内渗透压降低**」→ 溶破（与常见教材表述不同）；③ p40 同时列 `MIRL = CD59 = HRF20` 与「同源限制因子（HRF）」并附注 `CD59 also known as HRF20`，四名是否同义未讲清；④ p17 的抗体活化 C1q 能力序列**未列 IgG4**；⑤ p8 补体受体清单只到 CR1～CR5，未说明 p48 出现的 **CR2 = CD21** —— 全部以 `> [!warning]` 保留原样
- **讲义未展开的内容不补**：补体受体的分布与功能、补体与凝血/纤溶/激肽交互的分子节点、补体抑制剂的临床应用、HAE/PNH 的临床细节、C3d-CD21 协同刺激的具体信号通路 —— 各节点以 `> [!warning]` 列出缺口
- 讲义 p48 的**英文图注**（C3 片段 + BCR + CD21 提高亲和力）已译为中文要点并注明出自该页英文图注

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | 新建 Lecture 05；Course.md 已回写；README 索引 = 46；Lecture 引用 S-LEC-018 |
| 5.1.8 计数与索引 | 学科概念节点 46 = README 索引 46（第一章 4 + 第三章 12 + 第四章 15 + 第五章 15） |
| 5.1.9 陈旧「（待建）」 | 0 |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 16 处；15 个新节点全部裸基名、无 `../` |
| 课堂测试题 | Q-Imm-25~32 八题齐备；`03 抗原` 的不成立声明已修正 |
| 编码与 EOL | 所有改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

## 2026-09-22 — /ingest 医学微生物学 第 2 章 细菌的生理

> 用户要求：「/ingest 微生物学 细菌的生理」。

### 来源

`02_Raw/Lectures/Medical Microbiology/3 第2章 细菌的生理 .pdf`（51 页 PPT，赵巍，病原生物学系，2026 秋）→ 登记为 **S-LEC-017**。
课程层编号沿用「讲次序号」口径（01 绪论 · 02 细菌的形态与结构），故本讲为 **`03 细菌的生理`**，frontmatter `chapter: 3`。

### Created：16 个概念节点（医学微生物学 24 → 40；全库 162 → 178）

| 组 | 节点 | 来源页 |
|----|------|--------|
| 理化性状与营养（4） | `Bacterial Physicochemical Properties` · `Bacterial Nutritional Requirements` · `Bacterial Nutrient Uptake` · `Bacterial Nutritional Types` | p3、p5–p6、p8–p10 |
| 生长条件与规律（4） | `Factors Affecting Bacterial Growth` · `Bacterial Oxygen Requirements` · `Bacterial Growth and Reproduction` · `Bacterial Growth Curve` | p11–p14、p16–p19 |
| 代谢（3） | `Bacterial Energy Metabolism` · `Bacterial Biochemical Reactions` · `Bacterial Anabolic Products` | p20–p35 |
| 人工培养与分类（5） | `Bacterial Culture Methods` · `Culture Medium` · `Bacterial Growth in Culture` · `Colony` · `Bacterial Taxonomy and Nomenclature` | p37–p50 |

### Updated

- **新建 `08_Courses/Medical Microbiology/Lectures/03 细菌的生理.md`**：含 Lecture Overview / 章节目标 / 章节结构 / 五节正文 / Class Notes / Related Medical Knowledge（16 节点 + 跨章）/ Related Questions；正文 `详见 [[Node]]。` 18 处
- **`08_Courses/Medical Microbiology/Course.md`**：Lectures 清单追加第 3 讲；`Source` 段补第 2 章 PPT
- **`03_Concepts/Medical Microbiology/README.md`**：`已建节点（24）` → **`（40）`**，新增「细菌学 · 生理（第 2 章）」16 行逐节点索引
- **`99_System/Source-Registry.md`**：新增 `S-LEC-017`
- **计数回写**：`AGENTS.md` §4（24 → 40）、`00_Dashboard/Home.md`（162 → **178 节点**；医学微生物学 24 → 40）、`99_System/Knowledge-Status.md`（162 → 178）

### 本讲特点：章节目标是**来源直接给出**的（第二次）

讲义 p2 有**五条学习目标**（描述/阐述/复述/列举/描述），p51 另有「**本章重点与难点**」明确列出**掌握 / 熟悉 / 了解**三层。
因此本 Lecture 的 `## 章节目标` **直接引用讲义 p2 与 p51 原文**，**不套用** `> [!info] Clinical Reasoning`（inference）标注 —— 与 `04 抗体` 同属自带掌握层级的课件。

### 结构与取舍（不发明医学事实）

- **节点粒度对照讲义实况**：`Colony`（菌落）**独立成节点** —— 因为 p51 明确把「掌握细菌菌落概念及意义」列为**掌握**；而 `Uses of Bacterial Culture`（人工培养的用途，p47）**不单建**，收在 `Bacterial Culture Methods` 内（讲义仅 4 行）
- **`Factors` 与 `Oxygen Requirements` 分工**：p12 的「气体」既是 5 因素之一、又是学习目标第 3 条的独立主题 → 拆成两个节点，`Factors` 只留一句概述 + 链接，避免重复
- **讲义矛盾/未说明处一律标注，不代为判断**：① p5 成分比例只给「水 75%~90%、10%~25%」两档，未说明后者范围与各成分比例；② p6 未给细菌等电点测定方法与 G⁺ 更低的原理；③ p22 未说明厌氧呼吸与发酵的关系、未给戊糖磷酸途径产能数值；④ p24 糖发酵原理图只标两个「酶」字未给酶名；⑤ p28 编号从 3 直接跳到 **5**（缺 4）；⑥ p34 的合成代谢产物编号未从 1 起（p33 已用 1）；⑦ p48/p50 未标出「界」与「域」是否同一层级
- **讲义未展开的内容不补**：内毒素—外毒素系统对比表、外毒素分类、各类培养基配方、MALDI-TOF 与分子分型、细菌代谢的酶合成调节 —— 各节点以 `> [!warning]` 列出缺口
- **`type` 字段的取舍**：本讲 16 个节点一律用 **`physiology`**（讲义主题即「生理」，描述正常细菌生理，符合 AGENTS.md §5 的类型语义）。这与本学科第 1 章 24 个节点此前统一标 `pathophysiology` **不一致** —— 属既有的类型标注松散问题，已在报告中提出但**未擅自批量重标**（SOP §27）
- 讲义 p4、p15、p18、p24、p44、p50 等为**纯图片或示意图页**，只保留可读要点

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | 新建 Lecture 03；Course.md 已回写；README 索引 = 40；Lecture 引用 S-LEC-017 |
| 5.1.8 计数与索引 | 学科概念节点 40 = README 索引 40（学科基础 4 + 第 1 章 20 + 第 2 章 16） |
| 5.1.9 陈旧「（待建）」 | 0 |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 18 处；16 个新节点全部裸基名、无 `../` |
| 章节目标来源 | 引自讲义 p2 学习目标 + p51 本章重点与难点，**未**使用 inference 标注 |
| 编码与 EOL | 所有改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

## 2026-09-21 — /review 寄生虫 蛔虫与鞭虫（首次复习会话）

> 用户要求：「/review 寄生虫 蛔虫与鞭虫」。

### 产出

| 类型 | 内容 | 位置 |
|------|------|------|
| **复习会话记录** | `Session-2026-09-21-Ascaris-Trichuris` | `08_Courses/Human Parasitology/Reviews/` —— **本课程第一个 `Reviews/` 目录** |
| **题目** | `Q-Para-01` ~ `Q-Para-13`（13 道） | `05_Study/Questions/` |
| **闪卡** | `FC-Para-01` ~ `FC-Para-08`（8 张） | `05_Study/Flashcards/` |
| **跨课程队列** | 「蛔虫与鞭虫」条目 + 6 次间隔重复排期 | `05_Study/Review/README.md`（原为「暂无登记 — 由 `/review` 生成」） |
| **索引** | Questions / Flashcards README 各增 Para 分组；命名规范补 `Para` 课程代号 | `05_Study/` |
| **课程层** | Course.md `## Reviews` 由「_（暂无）_」改为会话链接 | `08_Courses/Human Parasitology/Course.md` |

### 题型覆盖（AGENTS.md §22 五类全覆盖）

| 类型 | 题号 | 数量 |
|------|------|------|
| Recall | Q-Para-01 · 03 · 04 · 08 | 4 |
| Interpretation | Q-Para-06 · 07 | 2 |
| Differential | Q-Para-02 · 12 | 2 |
| Clinical Reasoning | Q-Para-09 · 10 · 11 | 3 |
| Management | Q-Para-05 · 13 | 2 |
| **合计** | | **13** |

其中 `Q-Para-01`~`05` 是**讲义 slide 44 的 5 道原始思考题原文转写**（本课件无内嵌选择题，与免疫学 PPT 不同）；`Q-Para-06`~`13` 为基于 9 个概念节点的扩展题。

### 分层遵循（`05_Study/Review/README.md` 的 2026-09-14 定案）

| 层 | 位置 | 本次动作 |
|----|------|----------|
| **调度**（该做什么、何时） | `05_Study/Review/` | 登记队列条目 + 6 次复习排期（当天 / +1d / +3d / +7d / +14d / +30d） |
| **记录**（做了什么） | `08_Courses/<Course>/Reviews/` | 新建会话记录（Review Scope / Self-Test Results / Knowledge Gaps / Next Review 等） |

### 取舍与合规

- **不发明医学事实**：全部答案限定在 **9 个概念节点 + Lecture 02** 之内。讲义未给的内容 —— 蛔虫日产卵量数值、各并发症发生率、Loeffler 综合征诊断标准、鞭虫病虫负荷分级阈值 —— 一律在题解/闪卡中写明「**讲义未给出**」，不补
- **不收录剂量**：本学科 README 规定「本知识库不存储具体剂量」→ 管理类题（Q-Para-05 / 13）与全部闪卡只写药物**名称**，并附「须核对现行 WHO 指南与药品说明书」声明；脚本已核验 21 个新文件中**无任何数字剂量**
- **自构病例已显式标注**：`Q-Para-11`（儿童重度鞭虫感染 → 直肠脱垂）为**自构病例**，题解中标注「自构，用于综合讲义所述机制」；`Q-Para-09` 用讲义 slide 45–50 的**真实病例**，全部实验室与影像数据原样保留
- **学习目标带 inference 标注**：本课件**没有重点难点页**（与同日 `04 抗体` 相反），故会话记录的三层目标是推断，已加 `> [!info] Clinical Reasoning` 声明
- **两处口径差异未被抹平**：① 鞭虫「人是唯一传染源」（虫种层面）vs 蛔虫「粪便内含受精蛔虫卵的人」（病原学层面）—— 闪卡 `FC-Para-07` 的共同点栏**未**把「人是唯一传染源」写成两者共有；② 讲义 slide 49「胆道蛔虫病以青壮年多见」与 slide 50 针对**该例老年不典型患者**的机制分析不可混用，题解中已点明

### §24 复习优先级（逐项落实）

| 优先级 | 本次落实 |
|--------|----------|
| 最近新增知识 | 本讲即 2026-09-15 `/ingest` 的 `S-LEC-014`（9 节点） |
| 最近错题 | 无（首次 `/review`）→ 会话记录与两个索引均留了错题回填位 |
| `Needs Review` | 单列一节，汇总讲义 6 项未决疑问（鞭虫传染源口径、虫卵发育阶段、食管/咽管表述、病例机制适用范围、讲义未展开项、剂量不收录） |
| `Knowledge Gap` | 本讲 6 项覆盖缺口 + 待建虫种/药物节点，并指向下一讲（钩虫·蛲虫，课件已在库但未 `/ingest`） |
| 长时间未复习 | 首次复习，按间隔重复排期 |
| 高频临床主题 | 胆道蛔虫病占 2 道临床推理题（典型 vs 不典型） |

### 验证

| 检查项 | 结果 |
|--------|------|
| 文件产出 | 13 题 + 8 闪卡齐备且编号连续；会话记录含模板四个必备小节 |
| 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 本学科剂量规则 | 21 个新文件**无任何数字剂量**（脚本检出） |
| 题型覆盖 | §22 五类齐全 |
| 索引完整性 | Questions README 收录 13 题、Flashcards README 收录 8 张 |
| 编码与 EOL | 所有改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

> **遗留提示**：医学免疫学第四章 抗体（2026-09-21 `/ingest`）与病理学第三章 局部血液循环障碍（2026-09-18 `/ingest`）**均尚无复习会话**，已作为候选列入 `05_Study/Review/README.md` 的队列。

## 2026-09-21 — /ingest 医学免疫学 第四章 抗体（免疫球蛋白）

> 用户要求：「/ingest 免疫学 抗体」。

### 来源

`02_Raw/Lectures/Medical Immunology/第四章 抗体.pdf`（46 页 PPT，杨艳艳，基础医学院免疫学系，2026 秋）→ 登记为 **S-LEC-016**。
课程层 Lecture 编号沿用「章号 = 编号」口径，故本讲为 **`04 抗体`**（第二章仍未摄入，编号无 02）。

### Created：15 个概念节点（医学免疫学 16 → 31；全库 147 → 162）

| 节 | 节点 | type | 来源页 |
|----|------|------|--------|
| 第一节 Ig 的结构 | `Antibody` · `Variable Region and Constant Region` · `Ig Enzymatic Fragments` | physiology | p4、p6–p16、p23 |
| | `Immunoglobulin Antigenicity` · `J Chain and Secretory Piece` · `Immunoglobulin Superfamily` | physiology | p17–p22、p25 |
| 第二节 Ig 的生物学活性 | `Antibody Functions` | physiology | p27–p31 |
| 第三节 各类 Ig | `IgM` · `IgG` · `IgA` · `IgD` · `IgE` | physiology | p33–p38 |
| 第四节 人工制备抗体 | `Polyclonal Antibody` · `Monoclonal Antibody` · `Engineering Antibody` | physiology | p40–p44 |

### Updated

- **新建 `08_Courses/Medical Immunology/Lectures/04 抗体.md`**：含 Lecture Overview / 章节目标 / 章节结构 / 四节正文 / Class Notes / Related Medical Knowledge（15 节点 + 跨章）/ Related Questions；正文 `详见 [[Node]]。` 13 处
- **`08_Courses/Medical Immunology/Course.md`**：Lectures 清单追加第 4 讲；`Related Medical Knowledge` 由 16 扩为 **31 节点**；`Knowledge Gaps` 的已摄入章节补第四章；**`Source` 段补上此前遗漏的第三章 PPT 与 `S-LEC-010`**
- **`03_Concepts/Immunology/README.md`**：节点清单 `16` → **`31`**，新增「第四章 · 抗体」分组（按四节分列）；「待建节点」中删除已建的 `Antibody / Immunoglobulin`；「未摄入章节」说明补第四章
- **`99_System/Source-Registry.md`**：新增 `S-LEC-016`
- **计数回写**：`AGENTS.md` §4（16 → 31）、`00_Dashboard/Home.md`（147 → **162 节点**；免疫学 16 → 31）、`99_System/Knowledge-Status.md`（147 → 162）

### 本讲特点：章节目标是**来源直接给出**的

讲义 p2「重点难点」**明确标注了三层掌握程度** —— 掌握：抗体的结构及功能；熟悉：抗体的多样性、免疫原性及决定因素；了解：人工制备抗体的方法。
因此本 Lecture 的 `## 章节目标` **直接引用讲义 p2**，**不套用**其他章节使用的 `> [!info] Clinical Reasoning`（inference）标注 —— 这是本库首次遇到自带掌握层级的课件。

### 结构与取舍（不发明医学事实）

- **节点粒度对照讲义四节目录**：五类 Ig 各建独立节点（含量 / 结构 / 膜型与分泌型 / 临床意义各自独立）；而 `CDC`、`ADCC`、`调理作用` **不单建节点** —— 讲义对它们只有名称级描述（p28 一行 + p29 效应细胞标注「NK \ Mφ」），按 SOP §2.3 收在 `Antibody Functions` 内，待后续讲次展开时再独立
- **`Ig ⊃ Ab` 关系已标注为推导**：讲义 p4 给出两个定义但未显式写出包含关系，Lecture 与 `Antibody` 节点均以引用块呈现并注明「由两个定义推出、非讲义原句」
- **讲义自相矛盾/未说明处一律标注，不代为判断**：① IgE「CH2 和 CH3 结构域」结合 FcεRⅠ，而 p14 说 ε 链含 CH1～CH4 → 标 warning；② CH「9 种」的具体构成讲义未列；③ 高变区三区段（27～31、49～53、94～98）用哪套编号体系讲义未注明；④ p43 的 HGPRT 缺陷型在选择培养基中的作用机制未说明；⑤ p44「为什么人源化？」以设问提出但**未作答** → 只提示可结合「同种型抗原」跨节点思考，并标注该关联非讲义陈述
- **ADCC 效应细胞的表述差异已标注**：讲义 p29 把效应细胞标为 NK 与 Mφ，未区分二者角色 —— 本库不代为补充

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | 新建 Lecture 04；Course.md 已回写（并补上遗漏的第三章来源）；README 索引 = 31 |
| 5.1.8 计数与索引 | 学科概念节点 31（第一章 4 + 第三章 12 + 第四章 15） |
| 5.1.9 陈旧「（待建）」 | 0 |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 13 处；15 个新节点全部裸基名、无 `../` |
| 章节目标来源 | 引自讲义 p2 重点难点，**未**使用 inference 标注 |
| 编码与 EOL | 所有改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

> **顺带修复 1**：`08_Courses/Medical Immunology/Course.md` 的 `## Source` 段此前**只有第一章 PPT 与 S-LEC-004**，第三章的 PPT 与 `S-LEC-010` 从未登记（Course.md 自身 `Knowledge Gaps` 却写着「已摄入第三章」）—— 已补齐。
> **顺带修复 2**：第三章有 **5 个节点缺失 `## Related Concepts` 整节**（`Antigen` · `Epitope` · `Antigen Classification by Origin` · `T Cell Epitope vs B Cell Epitope` · `TD-Ag vs TI-Ag`）—— 该节为 `99_System/Templates/07_Pathophysiology.md` 的必备小节，且 §3.5.5 要求的「概念节点 → 所属章节 Lecture」回链正写在其中。已为 5 个节点补建该节（首行 `[[03 抗原]]`，只加链接、未增删任何医学内容）。
> **遗留警告**：免疫学 31 个节点之间单向链接 **45 条**（§5.2 建议项）。本次已把有实义的补齐（五类 Ig **两两全互链**、`Antigen ← Antibody`、`Epitope ← Variable Region and Constant Region`、`Cross-Reaction ← Polyclonal Antibody`）；其余绝大多数是「具体节点 → 泛化枢纽节点」方向（`X → Antibody` 13 条、`X → Antigen` 约 15 条），属枢纽式单向，反向补齐等于让枢纽节点罗列全部子节点 —— 那是 README 节点索引的职责，按 AGENTS.md §10 保留并报告。

## 2026-09-18 — /ingest 病理学 第三章 局部血液循环障碍

> 用户要求：「/ingest 病理学 血障」。

### 来源

`02_Raw/Lectures/Pathology/笔记—血障.docx`（311 段，优课联盟 UOOC 慕课笔记，2026 秋）→ 登记为 **S-LEC-015**。
沿用第一、二章的 docx 提取口径（stdlib `zipfile` + 段落号索引，`[NNN]` 编号与既有节点引用格式一致）。
本次为求无 XML 泄漏改用 `ElementTree` 重抽（原正则法在第 310 段漏出 `<w:tabs>` 标签残留），两法段落号一致。

### Created：21 个概念节点（病理学 48 → 69；全库 126 → 147）

| 节 | 节点 | type | 来源段落 |
|----|------|------|---------|
| 第一节 充血和淤血 | `Hyperemia` · `Congestion` · `Pulmonary Congestion` · `Hepatic Congestion` | pathophysiology | 006–065 |
| 第二节 出血 | `Hemorrhage` | pathophysiology | 066–080 |
| 第三节 血栓形成 | `Thrombosis` · `Virchow's Triad` · `Thrombus Types` · `Thrombus Outcome` · `Thrombosis Consequences` · `Disseminated Intravascular Coagulation` | pathophysiology | 081–187 |
| 第四节 栓塞 | `Embolism` · `Pulmonary Embolism` · `Systemic Arterial Embolism` · `Fat Embolism` · `Gas Embolism` · `Amniotic Fluid Embolism` | pathophysiology | 188–255 |
| 第五节 梗死 | `Infarction` · `Anemic Infarction` · `Hemorrhagic Infarction` · `Septic Infarction` | pathophysiology | 256–310 |

### Updated

- **新建 `08_Courses/Pathology/Lectures/03 局部血液循环障碍.md`**：含 Lecture Overview / 章节目标 / 章节结构 / 五节正文 / Class Notes / Related Medical Knowledge（21 节点 + 跨章）/ Related Questions；正文 `详见 [[Node]]。` 21 处
- **`08_Courses/Pathology/Course.md`**：Lectures 清单追加第 3 讲；`Related Medical Knowledge` 由 48 扩为 **69 节点**（新增第三章 5 组）；`Knowledge Gaps` 增列「第三章遗留」；`Source` 段补 `.docx` 与 S-LEC-015；**顺带修掉 2 处指向已删除小节的陈旧导航说明**（`## 本章知识导航`，该小节 2026-09-14 已按 §3.5.5 移除）
- **`03_Concepts/Pathology/README.md`**：`已建节点（48）` → **`（69）`**，新增「第三章 局部血液循环障碍」5 组、21 行逐节点索引；「学科范围」中第三章由「（待 /ingest）」改为已建并逐节点链接；「待建节点」中删除第三章条目、改为「第三章遗留（讲义未覆盖）」
- **`99_System/Source-Registry.md`**：新增 `S-LEC-015`
- **计数回写**：`AGENTS.md` §4（48 → 69）、`00_Dashboard/Home.md`（126 → **147 节点**；病理学 48 → 69）、`99_System/Knowledge-Status.md`（126 → 147）

### 结构与取舍（不发明医学事实）

- **讲义只有一个显式节标题**：`第五节 梗死`（另有小节号 `一、充血`）。第二节～第四节的标题在讲义中**不存在** —— Lecture 内以 `> [!warning] 讲义结构说明` 明确标注哪些标题是原文、哪些是按内容边界倒推，未伪造节标题（SOP §3.5.6）
- **讲义未覆盖第六节 水肿**：仅在开篇导图与「淤血性水肿 / 淤血性积液」中提及 → 不建节点，记入 README「第三章遗留」与 Course `Knowledge Gaps`
- **不单建亚型节点**（§2.3）：四种血栓（白 / 混合 / 红 / 透明）合为一个 `Thrombus Types` 节点（它们是同一延续性血栓的头/体/尾三段），而**不**照第一章坏死亚型的先例拆分；三种梗死则按讲义分节独立成节点
- **脑梗死的归属存疑已如实标注**：讲义把脑梗死排在「（一）贫血性梗死」之后，但脑是**液化性坏死**而脾/肾/心为凝固性坏死 → 节点内以 `> [!warning]` 说明讲义未作归属判断，未替讲义下结论
- **讲义未给出的内容一律不补**：DIC 的诊断标准/分期/实验室指标、羊水栓塞发生率与病死率、脂肪栓塞综合征（FES）诊断标准、肺栓塞危险分层与抗凝溶栓指征、（羊水栓塞）抢救流程 —— 各节点以 `> [!warning]` 列出缺口
- **讲义只提问不给答案**：`讨论：术后久卧，如何预防下肢静脉血栓形成？`（[126]）在 `Thrombosis` 节点如实记录为讲义提问，**未自行作答**
- 讲义正文的缩写（PLT / RBC / WBC / cap / A / V / En）原样保留并在首次出现处以中文标注；讲义「淤血性硬化」一语**未**被升格命名为「淤血性肝硬化」

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | 新建 Lecture 03；Course.md 已回写并清除陈旧导航说明；README 索引 = 69；Lecture 引用 S-LEC-015 |
| 5.1.8 计数与索引 | 学科概念节点 69 = README 索引 69（第一章 22 + 第二章 26 + 第三章 21） |
| 5.1.9 陈旧「（待建）」 | 0 |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 21 处；21 个新节点全部裸基名、无 `../` |
| 编码与 EOL | 29 个改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

> **顺带清理**：`03_Concepts/Pathology/README.md` 的「已建节点」段下原有一个只含 `（待建）Pathology`（未链接文本）的「学科基础」小节 —— 该条目本身在文末「待建节点」中已列，已从「已建」段移除，改为一行指引（§5.1.8 精神：已建段不列待建项）。
> **遗留警告**：第三章节点之间单向链接 **14 条**（§5.2 建议项）。已把其中有实义的 6 条补齐（`Embolism ← Thrombosis / Thrombus Types`、`Thrombosis ← Thrombus Outcome / DIC`、`Thrombus Types ← Thrombosis Consequences`、`Anemic Infarction ← Systemic Arterial Embolism`）；其余为「上游概念 → 下游罕见并发症」方向的弱关联，按 AGENTS.md §10「不为凑链接而链接」保留并报告。

## 2026-09-15 — /ingest 人体寄生虫学 医学蠕虫学 第一章 线虫（蛔虫与鞭虫）

> 用户要求：「/ingest 人体寄生虫学 蛔鞭」。

### 来源

`02_Raw/Lectures/Human Parasitology/临床第二讲蛔鞭.ppt`（50 页 PPT，课件版本 2022）→ 登记为 **S-LEC-014**。
本讲 = 医学蠕虫学第一章「线虫」的第一讲：第一节 概论 + 第二节 似蚓蛔线虫 + 第三节 毛首鞭形线虫，末页附胆道蛔虫病病例分析。课程学时分配中「线虫概论及线虫各论」共 6 h，本讲为开篇。

**提取方式**：来源是旧版二进制 `.ppt`，`pypdf` 不适用 → 改用 **PowerPoint COM** 提取全部文本（含表格，50 页）并导出 50 张幻灯片 PNG 备查。
课件**属性（Title/Author/Company 全空）与首页均未标注讲者姓名** → 未代为署名，`instructor` 记为「病原生物学教研室（课件未标注讲者）」。

### Created：9 个概念节点（人体寄生虫学 11 → 20）

| 组 | 节点 | type | 来源 slide |
|----|------|------|-----------|
| 概论 | `Nematode` · `Larva Migrans` | pathophysiology | 2–9、8/10 |
| 蛔虫 | `Ascaris lumbricoides` | pathophysiology | 10–19、32–34 |
| | `Ascariasis` | disease | 20–31 |
| | `Biliary Ascariasis` · `Loeffler Syndrome` | disease | 24–26、45–50 / 20–21 |
| 鞭虫 | `Trichuris trichiura` | pathophysiology | 35–39、43 |
| | `Trichuriasis` | disease | 40–43 |
| 检查 | `Stool Egg Examination` | test | 31、43 |

### Updated

- **新建 `08_Courses/Human Parasitology/Lectures/02 蛔虫与鞭虫.md`**（本课程第 2 个 Lecture）：含 Lecture Overview / 章节目标 / 章节结构 / 三节正文 / 病例分析 / Class Notes / Related Medical Knowledge（9 节点 + 总论）/ Related Questions；正文用 `详见 [[Node]]。` 8 处
- **`08_Courses/Human Parasitology/Course.md`**：Lectures 清单追加第 2 讲；`Related Medical Knowledge` 由 11 节点分组清单扩为 **20 节点**；`Source` 段补 `.ppt` 与 S-LEC-014
- **`03_Concepts/Human Parasitology/README.md`**：`已建节点（11）` → **`（20）`**，新增「线虫各论 · 第 1 章 蛔虫与鞭虫（9）」分组索引；待建清单移除已建的 `Ascaris lumbricoides` / `Ascariasis` / 粪便虫卵检查
- **`99_System/Source-Registry.md`**：新增 `S-LEC-014`
- **计数回写**：`AGENTS.md` §4（11 → 20）、`00_Dashboard/Home.md`（117 → **126 节点**）、`99_System/Knowledge-Status.md`（117 → 126，并修掉该文件遗留的一处 `活跃概念节点 100` 陈旧值）

### 取舍与不确定性（不发明医学事实）

- **不收录药物剂量**：讲义给出具体给药方案（如鞭虫用丙硫咪唑）。按本学科 README「抗寄生虫药物」段的明确规定「本知识库**不存储具体剂量**」，9 个节点一律只写**药物名称**，并各加 `> [!warning]` 指向该规则与「用药前须核对指南」（AGENTS.md §3）
- **`Endotoxin` 式的合并判断（§2.3）**：肺蛔虫症（Loeffler 综合征）与胆道蛔虫病**独立建节点** —— 前者是具独立命名的综合征且会在钩虫 / 粪类圆线虫讲次重复出现，后者讲义用 6 页病例分析专门展开；而蛔虫的其余并发症（肠梗阻、胰腺炎、阑尾炎、肝蛔虫病）**不单建**，作为 `Ascariasis` 的一节
- **`Larva Migrans` 是薄节点**：讲义仅在 slide 8 与 slide 10 两处零散提及，节点内以 `> [!warning] 讲义覆盖度` 显式声明，未补机制或分类；并额外声明 slide 20 的「异位损害（Ectopic lesion）」属**蛔虫自身幼虫**表述、不得与幼虫移行症混同
- **讲义内部不一致原样保留**：Loeffler 综合征在讲义中有四种写法（肺蛔虫症 / Loeffler 综合征 / Loffler's syndrome / 蛔蚴性肺炎），节点专设「名称表述」小节声明，未擅自统一；slide 35 的「腹泄、腹疼」按规范用字写作「腹泻、腹痛」
- **静默更正已回填说明**：讲义 slide 10 把犬弓首线虫拼作 `Tosocara canis`，节点按规范学名 `Toxocara canis` 书写并**注明讲义原文拼写**；slide 17 英文表的「60 m45m」缺 μ，按 slide 15/16 补全为 60 × 45 μm（数值未改）
- 讲义 p13/p25/p27/p28/p29/p30/p42 等为纯图片页，只保留可读要点；`Nematode` 的体壁与四大器官系统讲义只有条目无展开，未补描述

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | 新建 Lecture 02；Course.md 已回写；README 索引 = 20；Lecture 引用 S-LEC-014 |
| 5.1.8 计数与索引 | 学科概念节点 20 = README 索引 20（总论 11 + 线虫各论 9） |
| 5.1.9 陈旧「（待建）」 | 0 |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 8 处；9 个新节点全部裸基名、无 `../` |
| 本学科剂量规则 | 9 个节点**无任何数字剂量**（脚本检出） |
| 编码与 EOL | 16 个改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |

> **顺带修复**：`Biliary Ascariasis` 原含一条 `[[Larva Migrans]]` 链接 —— 胆道蛔虫病（成虫钻入胆道）与幼虫移行症无医学关联，属凑链接，已按 AGENTS.md §10 删除。
> **遗留警告**：同级节点单向链接 22 条（§5.2 建议项），绝大多数是「具体虫种节点 → 总论节点（`Medical Helminthology` / `Parasite Life Cycle`）」方向；反向补齐会给总论节点硬塞全部虫种链接，属 §10 禁止的凑链接，故保留并报告。

## 2026-09-15 — /ingest 医学微生物学 第 1 章 细菌的形态与结构（第二部分）

> 用户要求：「/ingest 微生物学 细菌的形态与结构2」。

### 来源

`02_Raw/Lectures/Medical Microbiology/1 2 第1章 细菌的形态与结构 2.pdf`（64 页 PPT，赵巍，2026 秋）→ 登记为 **S-LEC-013**。
第 1 章由**两次课**讲完：S-LEC-006（第一部分，16 页，形态学 + 结构总览）+ S-LEC-013（第二部分，64 页，结构分子细节 + 检查法）。

### Created：17 个概念节点（医学微生物学 7 → 24）

| 组 | 节点 | 来源页 |
|----|------|--------|
| 细胞壁（6） | `Bacterial Cell Wall` · `Peptidoglycan` · `Teichoic Acid` · `Outer Membrane` · `Lipopolysaccharide` · `Bacterial L-Form` | p16–p34 |
| 细胞膜 · 细胞质 · 核质（5） | `Bacterial Cell Membrane` · `Bacterial Cytoplasm` · `Bacterial Ribosome` · `Plasmid` · `Nucleoid` | p35–p40 |
| 特殊结构（4） | `Capsule` · `Flagellum` · `Pilus` · `Spore` | p41–p55 |
| 检查法（2） | `Gram Stain` · `Acid-Fast Stain` | p56–p59 |

### Updated

- **`08_Courses/Medical Microbiology/Lectures/02 细菌的形态与结构.md`**（186 → 386 行）：补入第二部分全部内容（细胞壁分子组成 / 细胞膜 / 细胞质 / 核质 / 四种特殊结构 / 第三节检查法）；`章节目标` 与 `章节结构` 重写（第三节由「本次 PPT 未覆盖」改为已覆盖）；`## Related Medical Knowledge` 扩为本章 22 个节点；`来源` callout 与 frontmatter `topics` 同步
- **`03_Concepts/Medical Microbiology/README.md`**：`已建节点（7）` → `已建节点（24）`，改为**分组 + 逐节点要点**索引（学科基础 4 / 细菌学 · 形态与结构 20 → 再分总论 3、细胞壁 6、胞内 5、特殊结构 4、检查法 2）
- **`Bacterial Structure.md`**：由「总览 + 两处 `（待补充）` 占位」升级为**枢纽节点**（新增子节点索引表）；三处待建标记清理完毕 —— `Bacterial Cell Wall` 与 `Gram Stain` 已建为实链、`Endotoxin` 不单建而改指 `[[Lipopolysaccharide]]`
- **`Bacterial Morphology.md`** · **`Bacterium.md`**：`Related Concepts` 补本章 Lecture 回链（§3.5.5）与新增节点链接
- **`08_Courses/Medical Microbiology/Course.md`**：`Related Medical Knowledge` 改为分组清单；`Source` 段补第二部分 PDF 与 S-LEC-013
- **`99_System/Source-Registry.md`**：新增 `S-LEC-013`
- **计数回写**：`AGENTS.md` §4（7 → 24）、`00_Dashboard/Home.md`（100 → 117 节点；MedMicro 7 → 24）、`99_System/Knowledge-Status.md`（100 → 117）

### 取舍与不确定性（不发明医学事实）

- **不单建 `Endotoxin` 节点**：讲义把 LPS 直接定义为「G⁻ 菌的内毒素」，内毒素的毒性与生物学活性组分（脂质 A）属 LPS 节点内容 —— 按 SOP §2.3 作为上层节点内容处理，避免亚型节点膨胀
- **讲义未给的机制一律未补**：革兰染色的**结果颜色判读**（讲义只有图题「革兰染色步骤及结果」，文本层无颜色描述）、染色作用时间/温度、芽胞 DPA 全称与分子机制、肽聚糖合成生化步骤、外膜孔蛋白分型 —— 均显式标注为讲义未展开
- **原文存疑处保留原文**：`Christain Gram`（疑为 Christian）保留讲义拼写、未静默更正；`membrane teichoic acid` 与 `LTA（lipoteichoic acid）` 讲义并列使用，未擅自合并
- 讲义 p46 为**无文本层**图片页（64 页中唯一 1 页）；p45 / p47 / p48 鞭毛马达内容零散，仅保留可读要点
- **讲义内部矛盾（需人工裁决）**：p21 写「A 群链球菌 M 蛋白」，p30 写「乙型链球菌 M 蛋白」—— 同一蛋白两种归属，已在 `Bacterial Cell Wall` 中按 p30 原文采用，未擅自合并
- **p28 厚度示意图的文本层丢配**：只剩「外膜 2-3nm / 肽聚糖 7-13nm / 20-80nm / 10~15nm」四个数值，与 G⁺/G⁻ 的配对关系丢失，节点内按 p27 表格（G⁺ 20~80nm、G⁻ 10~15nm）配对并如实说明依据
- **革兰染色的结果颜色未写入**：讲义文本层只有图题「革兰染色步骤及结果」，**无 G⁺/G⁻ 颜色描述** → `Gram Stain` 以 `> [!question] 待核` 标注，未按记忆补「紫色 / 红色」

### 验证（Ingest-SOP §5）

| 检查项 | 结果 |
|--------|------|
| 5.1.1 链接可解析（与 HEAD 逐文件对比） | **新增未解析链接 0** |
| 5.1.7 课程层同步 | Lecture 02 更新并列出全部 22 个本章节点；Course.md 已回写；Lecture 引用 S-LEC-013 |
| 5.1.8 计数与索引 | 学科概念节点 24（= README 索引 24；分组 4 + 20 = 24，子组 3+6+5+4+2 = 20） |
| 5.1.9 陈旧「（待建）」 | 0（清理 2 处：`Bacterial Cell Membrane` / `Bacterial Ribosome` 中的 `Bacterial Cell Wall`） |
| 5.1.12 链接写法 | Lecture 标题内 wikilink 0；`详见 [[Node]]。` 18 处；新节点全部裸基名 |
| 编码与 EOL | 无 U+FFFD、无已知夾变字；31 个改动文件 EOL 各自一致、无 CRLF 双写、均有尾换行 |
| 真自链 | 0 |

> **顺带修复的既有缺口**（非本次 ingest 引入）：`Medical Microbiology` / `Microbial Classification` / `Infection vs Transmission` / `Koch's Postulates` 四个绪论节点缺 `## Related Concepts` 与所属 Lecture（`01 绪论`）回链，已按 §3.5.5 补齐；`Course.md` 中 `[[03_Concepts/Immunology]]`（指向目录、不可解析）改为 `[[03_Concepts/Immunology/README|Immunology]]`。

## 2026-09-14 — 病理学概念链接接入正文 + 链接写法规范校准

> 用户要求：「把概念链接加进去」。

### 先量后改：全库链接写法基线

| 写法 | 全库计数 | 说明 |
|------|---------|------|
| 裸基名 `[[Atrophy]]` | **689** | 默认写法 |
| vault 根路径 `[[02_Raw/…]]` | 294 | 全部是指向来源文件 / Source-Registry |
| 相对路径概念链接 `[[../…]]` | **2** | 历史遗留，非规范 |

另测得：7/7 非病理学 Lecture 正文一律 `详见 [[Node]]。`；`章节目标` 表格 **0/7** 含链接；
`章节结构` 位于代码块内，Obsidian 不渲染其中的 wikilink。三者共同决定了本次的写入形状。

### 操作

**1. `03_Concepts/Pathology/README.md`「学科范围」章节目录全部可点击**

- 6 条章节目录行由纯中文名改为 `[[Node|中文名]]`，并把原先省略的总论节点补齐：
  `Cell Injury`（可逆损伤总论）、`Cell Death`（细胞死亡总论）、`Repair`（修复总论）、`Cell Cycle`；
  另把「各组织再生机制」展开为 6 个器官/组织节点，新增「特定病变」行（`Traumatic Neuroma` · `Keloid`）
- 效果：学科 README 的**章节目录**与下方**节点索引表**现在覆盖同一组 48 个节点

**2. 两个 Lecture 正文接入 48 个概念节点**

- 新增 **20 条 `详见 [[Node]]。` 行**（第一章 6 条、第二章 14 条），位置紧跟小节标题之后
- **22 处** `[[../../../03_Concepts/Pathology/X|X]]` → 裸基名 `[[X]]`：
  其中 5 处 bullet 内联链接解包为纯文本（`- **萎缩**（[[Atrophy|Atrophy]]）：` → `- **萎缩**：`，节点入口交给该节的 `详见` 行），
  3 处标题内链接移除（`### 坏死（[[Necrosis]]）` → `### 坏死`），表格内链接改为裸基名
- 覆盖结果：**48/48 概念节点**在两个 Lecture 正文 + 学科 README 中均可点击到达

### 顺带校准的两份规范

- `99_System/Ingest-SOP.md` **§3.4 重写**：旧版把 `[[../Immunology/Immune Dysregulation]]` 列为**推荐**写法，
  而那是全库仅 2 处之一 —— 规范落后于事实，正是病理学 Lecture 写成相对路径的根因。
  现改为「**裸基名默认 + 两个路径例外**」，并补入 Lecture 正文行与反例说明
- 新增 **§5.1.12** 后验项（Lecture / README 正文不得残留相对路径概念链接）+ **§7** 对应陷阱行
- `AGENTS.md` **§10** 补链接写法口径（裸基名默认、两例外、Lecture 用 `详见`）

### 验证

- 48/48 节点可点击；**新增未解析链接 0 条**（逐文件与 HEAD 版本对比）；真自链 0 条
- 混合 EOL 基线 **5**（未变）；三个文件均为纯 LF、无 BOM、有尾换行；CRLF 双写 0
- 残留「裸概念名」提示均为**规范要求保持纯文本**的位置：`章节目标` 表格（0/7 学科有链接）、
  `章节结构` 代码块（wikilink 不渲染）、正文散文与 `Class Notes`、frontmatter `topics`

## 2026-09-14 — 病理学 Lectures 向其他学科公约对齐

> 用户要求：「类比一下其他学科的 courses 中 lectures 下的章节是怎么做的，重新整理病理学」。

### 实测公约（先量后改）

对 9 个 Lecture 逐项统计后得到的公约：

| 小节 | 其他 7 个 Lecture | 病理学（上一轮我的改动） |
|------|------------------|------------------------|
| `Lecture Overview` · `章节目标` · `Class Notes` · `Related Questions` | 7/7 | ✅ |
| `章节结构` | 4/7 | ✅ |
| `Related Medical Knowledge` 内容 | **本章概念节点扁平清单**（CE 02 列 12 个、寄生虫 11 个、免疫 03 列 12 个…） | ❌ 被改成跨章跨学科引用，**无节点清单** |
| `本章知识导航`（分组 + 要点） | **0/7** | ⚠️ 仅病理学有 |
| `Knowledge Gaps` | **0/7** | ⚠️ 仅病理学有 |
| `来源与摄入记录` | **0/7** | ⚠️ 仅病理学有 |
| frontmatter `discipline:` | 6/7 | ❌ 缺 |
| frontmatter `aliases:` | **0/7** | ⚠️ 仅病理学有 |

**结论：上一轮我把「详细导航」理解成了自创小节，反而让病理学偏离了公约。** 其他学科的章内导航就是 `Related Medical Knowledge` 的节点清单，而「分组 + 要点」索引在任何学科的 Lecture 里都不存在。

### 操作（按用户选择的方案 A）

**1. 两个 Lecture 回归公约形状**

- `## Related Medical Knowledge` 恢复为**本章概念节点的扁平清单**（第一章 22 行、第二章 26 行），末尾附 1–2 条下一章 / 协作学科（与 `Medical Microbiology/01 绪论` 混排姊妹学科链接的写法一致）
- **删除** `## 本章知识导航` / `## Knowledge Gaps` / `## 来源与摄入记录` 三个自创小节
- frontmatter：**补 `discipline: Pathology`**（6/7 学科有而病理学缺）；**删除 `aliases`**（0/7 学科有，且链接已全部改用文件名，别名已无用）

行数：Lecture 01 296 → **234**；Lecture 02 354 → **277**。两个 Lecture 的小节集合现与 `Clinical Epidemiology` **完全一致**。

**2. 「分组 + 要点」索引下沉到学科 README（方案 A）**

`03_Concepts/Pathology/README.md` 的「已建节点」段重建为**学科节点索引**：两章共 9 个分组、48 行「概念 / type / 要点」表，保留原 MOC 的分组与要点。

> 信息无损：被删的 `Knowledge Gaps` 已在 `Course.md` 与 README 待建清单；`来源与摄入记录` 已在 Lecture 顶部 `> [!info] 来源` callout 与 Source-Registry；要点索引已进 README。

**3. 治理同步**

- `Ingest-SOP`（12 处）：§0 产出清单改为「Lecture 节点清单 + README 节点索引」；§3.1 归属说明重写（章内导航 → Lecture 的 `Related Medical Knowledge`；学科节点索引 → 学科 README）；§3.5.4 删掉 3 个自创小节、`章节结构` 降为「推荐（4/7）」、`Related Medical Knowledge` 明确为扁平节点清单；§3.5.5 增「Lecture 不重复 README 的要点表」；§5.1.7/§5.1.8 改为查 README 索引的分组数字；陷阱表新增「Lecture 自创小节」一行
- `Templates/17_Lecture.md` 按公约重写（补 `discipline`、去 `aliases`、去 3 个自创小节、`Related Medical Knowledge` 为节点清单、检查清单加入「先横向比对同类文件」）

### 修一处自身副作用

插入 README 时用了 LF 文本，而该文件原为 CRLF → 混用行尾数 5→6。已归一化为纯 LF（与 `03_Concepts/Pathology/` 目录内多数文件及 git 存储一致），混用行尾数**恢复 5（基线）**。

### 验证

| 指标 | 结果 |
|------|------|
| 病理学 Lecture 小节集合 | 与 `Clinical Epidemiology` **完全一致** |
| Lecture 自创小节（本章知识导航 / Knowledge Gaps / 来源与摄入记录） | **3 → 0** |
| README 节点索引 | 9 组 / **48 行**，分组数字全部 = 表内行数 |
| 未解析链接 | 38 → **36** |
| 真实自链接 / 陈旧 MOC 链接 / 陈旧待建标记 | 0 / 0 / 0 |
| 混用行尾 / 缺末尾换行 / CRLF 翻倍 | 5（基线）/ 0 / 0 |

## 2026-09-14 — 病理学结构对齐：章节导航从 03_Concepts 移入 08_Courses/Lectures

> 用户要求：「将每一章的详细知识导航放在 courses 的 lectures 下，而不是 concept 中，concepts 下只存放概念知识点」+「类比其他学科」。

### 现状诊断

盘点后确认 **Pathology 是唯一把章节导航页放在概念层的学科**：

| 学科 | `03_Concepts/<学科>/` | `08_Courses/<学科>/Lectures/` |
|------|----------------------|------------------------------|
| Immunology · Medical Microbiology · Human Parasitology · Clinical Epidemiology | 节点 + README | 章节内容 |
| **Pathology** | 节点 + README + **`Chapter 1 - ….md` / `Chapter 2 - Repair.md`** | 章节内容 |

另有 **54 个文件、约 79 处 wikilink** 指向这两个导航页（其中 22 条来自第一章的 22 个节点、26 条来自第二章的 26 个节点）。

### 操作

**1. 章节导航写入 Lecture（导航的唯一归属）**

两个 Lecture 各新增 4 个小节，内容取自原 MOC：

- `## 章节结构` — 本章在学科中的位置流程图
- `## 本章知识导航（22 / 26 个概念节点）` — 分组节点索引表（每组标题含节点数 + 逐节点「要点」）
- `## Knowledge Gaps（待建 / 需扩展）` — 本章待建 + 跨学科联动
- `## 来源与摄入记录` — 主来源 / 来源登记 / evidence_level / `/ingest` 完成状态

同时：
- 删除正文中 4 处 `> 详见 [[MOC#…]]` 指针（导航已在同一文件内，无需外跳）
- `## Related Medical Knowledge` 由「22 节点扁平清单」改为跨章跨学科导航（上一章 / 下一章 / 学科目录 / Course / 协作学科 / 原始课件）
- frontmatter 增加 `aliases`（`第一章` / `组织细胞适应与损伤` / `Cellular Adaptation and Injury`；`第二章` / `损伤的修复` / `Chapter 2`）—— **刻意不含 `Repair`**（`Repair.md` 为同名概念节点，避免歧义）

Lecture 01：205 → **296 行**；Lecture 02：245 → **354 行**

**2. 删除概念层的两个导航页**

`Chapter 1 - Cellular Adaptation and Injury.md`、`Chapter 2 - Repair.md` 已从 `03_Concepts/Pathology/` 删除。
该目录现为 **48 个概念节点 + README**，与其余 10 个目录结构一致。

**3. 重定向 64 处 wikilink（55 个文件）**

统一改为指向对应 Lecture，显示文本规范为 `第一章 · 组织细胞适应与损伤` / `第二章 · 损伤的修复`。
**特别注意**：裸 `[[Repair]]` 指向**概念节点** `Repair.md`，全程未被触碰。

**4. 治理同步**

- `Ingest-SOP`：§0 产出清单（不再有「章节 MOC」项）、§3.1 顺序与归属说明、§3.5.4 必含部分（新增 `## 章节结构` / `## 本章知识导航` / `## Knowledge Gaps` / `## 来源与摄入记录` 四行）、§3.5.5 双向链接（改为「概念节点 → 所属章节 Lecture」）、§5.1.7、§5.1.8（新增「概念层不得有导航页」检查）、2 条陷阱行
- `AGENTS.md`：§4 学科块说明、§10 双向链接表（`所属章节 MOC` → `所属章节 Lecture`）
- `03_Concepts/Pathology/README.md`：6 处「+ 1 个 MOC」改为「章节导航见该 Lecture」
- `Templates/17_Lecture.md`：按新结构重写模板（含 4 个新小节占位与更新后的检查清单）

### 本次操作中自捉并修复的 2 个缺陷

- **`Course.md` 自链接**：重定向把 `- 关联 MOC：[[第一章 MOC]]` 变成指向本 Lecture 自己的自链接 → 改为 `- 章节导航：本 Lecture 内（…）`
- **6 处相对路径多一级 `../`**：`03_Concepts/<学科>/README.md` 中的 `[[../../../08_Courses/…]]`、`[[../../../02_Raw/…]]` 实际已指到 **vault 的父目录**，因 Obsidian 相对路径失败时会回退到 basename 匹配，这些链接一直"看起来正常"、历次检查都没抓到 → 已修为 `../../`；`08_Courses/Medical Microbiology/Lectures/01 绪论.md` 的 `[[../Human Parasitology/Course]]` 修为 `../../`。
  → 已把「相对路径必须单独查层级、并断言不逃出 vault」写入 SOP §5.1.1。

### 验证

| 指标 | 结果 |
|------|------|
| `03_Concepts/<学科>/` 含导航页的目录数 | **7 → 0**（11 个目录全部只有节点 + README） |
| 指向已删章节 MOC 的残留链接 | **0** |
| 真实自链接 | **0** |
| 未解析链接 | 38（与改动前一致，均为刻意待建） |
| 相对路径逃出 vault | **12 → 0**（余下 8 处为 `Templates/17_Lecture.md` 占位符，按实例化位置设计） |
| 混用行尾 / 缺末尾换行 / CRLF 翻倍 | 5（基线）/ 0 / 0 |

## 2026-09-14 — 处理上一轮审计遗留的 7 项 Warnings

> 用户要求：「处理 warnings」。逐项处理上文「本次审计未修复的项」。

### W1 `.gitignore` 重构 —— 教材登记信息纳入版本控制

原写法是「忽略整个 `02_Raw/`，再用 `!` 放行 `Lectures/`」。**该写法对教材从未生效**：
gitignore 规定「父目录被排除时，无法重新包含其中的文件」，因此 `!02_Raw/Textbooks/**` 之类规则全部失效
（连 `!02_Raw/Lectures/**` 也只是"看起来"生效，实际仅一个预先提交的 README 被跟踪）。

改为只排除 `02_Raw/*`（直接子项）+ 逐级放行目录 + 最后统一忽略大体积二进制（pdf/pptx/ppt/docx/doc）。结果：

- 4 份教材登记 README（`S-TXT-001~004`）**进入版本控制**
- 另外 6 份此前不可见的登记 README 一并纳入（`02_Raw/README.md`、`Textbooks/`、`Guidelines/`、`Papers/`、`QuestionBank/`、`Lectures/Pathology/`）
- 全部 PDF / PPT / DOCX 仍被忽略（`02_Raw/**/*.pdf` 等），未改变"原始大文件不入库"的既有策略

### W2 补记 Medical Immunology 缺第二章

`08_Courses/Medical Immunology/Course.md` 与 `03_Concepts/Immunology/README.md` 均补明：
已摄入第一章（`S-LEC-004`）与第三章（`S-LEC-010`），**第二章未摄入**，因此 Lecture 编号为 01、03 而**无 02** ——
是"待 /ingest"而非"文件丢失"。

### W3 frontmatter 既有字段纳入清单

`Ingest-SOP` §3.2 新增 **§3.2.1 已用 frontmatter 字段清单**：把 `aliases` / `created` / `last_updated` /
`course` / `chapter` / `difficulty` / `related_concept` / `scope` / `method` / `registered_date` /
`archived_from` / `archived_date` / `source_file` / `processed_date` 等**既有字段**正式登记，
并注明 `updated` 属漂移拼写（应用 `last_updated`）。新增字段前须先查表并同步更新。

### W4 复习会话归属冲突 —— 按设计执行，移动文件

冲突事实：`05_Study/README`、`08_Courses/README` 与 `05_Study/Review/README` 三处口径不一致
（前两处说会话记录放 `08_Courses/<Course>/Reviews/`，第三处说放 `05_Study/Review/`），实际文件在后者。

按多数口径 + 设计意图执行：
- **移动** `05_Study/Review/Session-2026-09-07-Immunology-Overview.md` → `08_Courses/Medical Immunology/Reviews/`（该文件全部链接为根相对式，移动无断链）
- 重写 `05_Study/Review/README.md` 为**纯调度队列**，并加「调度 vs 记录」分层表
- 同步更新 `08_Courses/Medical Immunology/Course.md`、`Knowledge-Status` 两处引用
- 这是 `08_Courses/<Course>/Reviews/` 的首次启用（此前 5 门课均无该子目录）

### W5 明确双向链接规则，消除"未互惠出链"的误判

`AGENTS.md` §10 补入适用范围表：**同级概念节点之间应互链**；**导航页（MOC/README/Lecture）→ 概念节点天然单向**，
不要求也不应为了"对等"而回链枢纽；概念节点至少链回所属章节 MOC 一次。
并写明**度量口径**：统计"未互惠出链"必须排除 MOC/README/Lecture 发出的链接 ——
否则第一章 MOC 的 23 条枢纽链接会被误判为缺陷。`Ingest-SOP` §5.2 同步加入「互惠性抽查（仅限同级节点）」。

### W6 补建 4 个专科目录，打通 `specialties` 轴

原 12 个 `specialties` 取值只有 4 个能对应 `06_Specialties/` 目录。新建 4 个专科导航目录：
`Public Health and Preventive Medicine`(17 节点) · `Tropical Medicine`(11) · `Allergy`(13) · `Rheumatology`(1)，
共覆盖 42 个节点引用。**现 8/12 有目录**。

其余 4 个取值经核实**本就不应有临床专科目录**，已在 `03_Concepts/README` 白名单中分类说明：
`Pathology`(48)、`Immunology`(16) 属**已注册学科名**；`History of Medicine`(2)、`Evidence-Based Medicine`(1) 属**非临床方向**。
（仍待人工决定：是否移除与目录冗余的 `Pathology`/`Immunology` 取值。）

### W7 行尾补换行（254 个文件）

原 312 个 md 文件中 **255 个缺末尾换行**，造成 git 反复出现 `\ No newline at end of file` 噪音。已为 254 个补齐。

**副作用已修复**：`AGENTS.md` 是 CRLF 文件，追加裸 `\n` 导致末尾出现一个孤立 LF（混用行尾数 5→6）；
已改为补 `\r\n`，混用行尾数恢复 **5（基线）**。

### 本次自我校验

| 指标 | 结果 |
|------|------|
| 混用行尾文件 | **5**（与基线一致，未新增） |
| 缺末尾换行文件 | **0** |
| CRLF 翻倍残留 `\r\r\n` | **0** |
| `specialties` 取值有目录者 | **4/12 → 8/12** |
| 跟踪的 `02_Raw` 登记 README | 1 → **10** |

## 2026-09-14 — 全库隐形逻辑 bug 审计与按优先级修复（三阶段）

> 用户要求：「全面搜索知识库，分析是否存在隐形逻辑bug」 → 「按优先级修复」。
> 方法：7 轮静态不变量扫描 + 3 个语义审计员逐节点对照讲义原文（病理 51 文件 / 基础医学 34 节点 / 流行病学+学习层 26 文件）。
> 结果：14 项 CRITICAL、约 30 项 WARNING，分三阶段修复。

### Phase 1 — 结构性（消灭 ~60% 发现项，且防止复发）

**§5.1 后验新增 3 项检查（`99_System/Ingest-SOP.md` 340 → 374 行）**

- **§5.1.8 导航页与目录实际一致**：Discipline README 的「已建节点」占位符、待建清单是否仍含已建节点、MOC 分组数字是否等于表格行数、MOC 总数算式是否自洽、`AGENTS.md`/`Medicine MOC`/`Home`/`Knowledge-Status` 计数是否同步、布局类 README 的「暂不创建」是否已被事实推翻
- **§5.1.9 陈旧「（待建）」标记扫描**（附检出正则）
- **§5.1.10 归档层 status 一致性**（附检出命令）
- **§3.2 type 枚举修正**：补入 `physiology`（AGENTS.md 允许但 SOP 漏列）、`review_session`、`exam_topic`、`reference_source`、`processing_record`；并**定案统一用下划线**（旧文档写 `wrong-answer`/`clinical-pearl` 连字符，而模板实际用下划线 → 两种拼写会让筛选器漏项）
- 新增 **§5.1.11 `specialties` 取值合法**检查

**计数与标签漂移**

| 文件 | 修正 |
|------|------|
| `AGENTS.md` §4 | Pathology **22 → 48** 节点 |
| `07_MOCs/Medicine MOC.md` | Pathology 22 → 48 |
| `Chapter 1 MOC` | 「二、可逆性损伤 — 7 个节点」→ **8**（表内实列 8 行，含 Cell Injury 总论）；「已建概念节点 21 个」→ **22**（5+8+9=22）；「所有 21 个节点」→ 22 |
| `08_Courses/Pathology/Lectures/01` | 同步锚点 `#…— 7 个节点` → `#…— 8 个节点`（否则锚点失效） |

**「暂无」占位符腐烂（5 处）**

- `03_Concepts/Clinical Epidemiology/README.md`：原「已建节点 _（暂无）_」→ 列出 **17 节点**；待建清单移除已建项；Course 去掉「（待建）」；注册学科列表补入 Pathology 与本学科；注册信息「无 Concept 节点」→「已建 17 个」
- `03_Concepts/Human Parasitology/README.md`：原「暂无」→ **11 节点**；待建清单移除已建的「寄生虫生活史」
- `08_Courses/Human Parasitology/Course.md`：「暂无」→ 11 节点清单
- `03_Concepts/Immunology/README.md`：节点清单 4 → **16**（补抗原章 12 个）；待建清单移除已建的 Antigen
- `08_Courses/Medical Immunology/Course.md`：Related knowledge 4 → 16
- `03_Concepts/Diseases/README.md`：原「已有节点 _（暂无）_」→ 列出 `Diabetes Insipidus`
- `08_Courses/README.md`：删除「当前尚未提供真实课程表，**暂不创建任何具体课程目录**」（实际已建 5 门课），改为课程总表 + 已知缺口

**陈旧「（待建）」标记：11 处已删除**（目标文件已存在）
`Adaptive Immunity:155` · `Immune System:158` · `Cell Death:50,51` · `Fibrinoid Necrosis:55,67` · `Gangrene:81` · `Liquefactive Necrosis:69` · `Necrosis:123,124,131`

**归档层 status：67 个文件 `active` → `archived`**
同层原有 8 个文件已标 `archived`（Inbox-Archive），67 个（Concepts-Retired / Questions-Retired）从未更新 → `status = active` 查询会扫入退役知识。现归档层 75/75 一致。

**杂项结构**

- `07_MOCs/Infectious Disease MOC.md`：`updated:` → `last_updated:`（字段名漂移）
- `07_MOCs/Nephrology MOC.md`：2 条死链（归档文件加了日期前缀）→ 指向实际文件名
- `05_Study/Review/Session-…`：死锚点 `[[Immune Dysregulation#待建节点]]` 删除；复习计划 4/5/3/3 → 实际 **2/2/2/4**
- `08_Courses/Medical Immunology/Lectures/03 抗原.md`：锚点 `#抗原的基本特性` → `#抗原的基本特性（两大）`
- `Ch1 MOC`：`玻璃质酸` → `透明质酸`；`脑梗塞式自噬` → `自噬`
- `Ch2 MOC`：室壁瘤从「不利」改为按来源 [125] 与 `Scar Tissue` 的口径
- `02_Raw/lectures` → `02_Raw/Lectures`（**6 处 / 4 文件**；大写敏感平台会断链）
- **CRITICAL 歧义修复**：`Chapter 2 - Repair.md` 的 `aliases` 中删除 `Repair` —— 该文件 frontmatter 声明了此别名，正文却写「`Repair` 不作为本 MOC 别名」，且 `Repair.md` 同名存在（全库 7 条 `[[Repair]]` 歧义）。现全库文件名/别名冲突 = 0。

### Phase 2 — 内容级医学事实（逐条核对**原始讲义 PDF**后修正）

审计中先提取了 7 份讲义 PDF 的文本层（**均有文本层**），据此判定而非凭记忆：

| 节点 | 原问题 | 依据 | 修正 |
|------|--------|------|------|
| `Parasitic Infection Characteristics` | 「内脏幼虫移行症」举例写「弓形虫」 | 讲义 p48 定义限定**蠕虫幼虫**且**未给任何举例**；弓形虫为原虫（`Medical Protozoology`），无幼虫阶段 | 删除该举例，改「讲义未举例」+ 警示 callout |
| `Microbial Classification` | 古生菌被塞进「细菌（…）」括号内 | 讲义 p8 原文：**古生菌（archaea）· 细菌（bacterium）**为**并列**两支 | 改为「**古生菌** + **细菌**（细菌、支原体…）」+ 警示 |
| `Parasitic Zoonoses` | 断言「人兽共患包括新现、再现、动物源性」 | 讲义 p17–19 把三者作为**同节并列主题**，非包含关系 | 定义收窄为动物源性 + 警示 |
| `Medical Arthropodology` | 「蜱螨纲」与「蛛形纲」并列 | 蜱、螨属**蛛形纲**；且讲义**未涉及**纲级分类 | 合并修正 + 明确标注「不在讲义范围内，待教材核对」 |
| `Fatty Change` | `[[Necrosis\|肝硬化]]` 指向坏死节点 | `Necrosis` 节点无肝硬化内容 | 改为 `[[Cirrhosis\|肝硬化]]（待建）` |
| `Pathologic Calcification` | `[[Coagulative Necrosis]]（结核→干酪样坏死→钙化）` 链接与注解矛盾 | 该链讲的是干酪样坏死 | 改为 `[[Caseous Necrosis]]` |
| `Q-Imm-08` | 表列「正常范围 5–6%」却给 4% 打 ✅、「0.2%」却给 0.5% 打 ✅，并断言「所有数据都在参考范围内」，与下方干扰项分析「应在 ≥5% 才考虑升高」冲突 | 讲义 p51 **确实**写「嗜酸性粒细胞（5-6%）」「嗜碱性粒细胞（0.2%）」→ 节点忠实，**缺陷在题目**把它当判定阈值 | 该列改标为「讲义所述占比」、去掉自相矛盾的 ✅、加修正警示；选项顺序 ACBD → **ABCD** |
| `Innate Immunity` | 占比数值未标口径 | 同上 | 加警示说明这些是**典型占比而非判定阈值** |
| `Cellular Aging` | 「端粒缩短」与「叠加损伤性、营养性多因素」为来源未述内容却写成事实 | 讲义 PARA 102–107 只给特征名与结局 | 删除 + `> [!info] Clinical Reasoning` 说明 |
| `Cell Death` | 引用范围 PARA 228–230 覆盖不到其酶学表 | 酶学表实际在 PARA 243–248 | 补全引用范围 |
| `Diabetes Insipidus` | 唯一来源 `02_Raw/Lectures/尿的生成与排出-2026-春.pdf` **全库不存在** | 全库检索无此文件 | `source_status: needs_review` → **`unsourced`** + 来源缺失警示 |

### Phase 3 — 治理与设计

- `03_Concepts/README.md` 新增「`specialties` 允许值」白名单：明确区分 ① `06_Specialties/` 临床专科 ② 已注册学科名 ③ 无目录的应用方向（Tropical Medicine 等）
- **未执行（留待人工决策）**：是否移除 64 个节点中与目录冗余的 `specialties: Pathology/Immunology`；是否为 `Tropical Medicine`（11 节点）与 `Public Health and Preventive Medicine`（17 节点）补建 `06_Specialties/` 目录

### 审计中发现并修复的**本次操作自身缺陷**

- 我的两个修复脚本对「从字节解码、未做换行归一」的文本执行了 `replace("\n", nl)`，
  对 CRLF 文件会把 `\r\n` 变成 `\r\r\n` → `Cell Death.md` 行数被翻倍（64 → 123）。
  已定位并修复（`\r\r\n` → `\r\n`，全库扫描确认仅此 1 个文件受影响），并改用**字节级**替换重写全部后续脚本。
  → 已记入 SOP §3.3 风险表同类问题；后续 8 个修复脚本均以字节操作，复检 `\r\r\n` = 0。

### 本次审计**未修复**的项（低优先或需决策）

- 7 个早期 Lecture 缺 `chapter:`、6 个缺 `## 章节目标` —— 已委派补齐（Phase 1 收尾）
- `05_Study/Review/` 与 `08_Courses/<Course>/Reviews/` 的复习会话归属冲突（两处 README 口径不一致）
- 61/102 概念节点存在未互惠出链（AGENTS.md §10；多为 MOC 枢纽的正常单向链接）
- `Medical Immunology` 课程 Lecture 编号缺 02（该章未 /ingest）
- `specialties` 轴对齐（见 Phase 3 待决策项）
- 归档层 `archived_from` / `archived_date` 等遗留字段未纳入 `AGENTS.md` 字段表

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
| [[Gangrene]] | pathophysiology | 坏疽（干/湿/气） |
| [[Apoptosis]] | pathophysiology | 调式（调引与调小体） |

> **节点计数：21 个 pathophysiology + 1 个 MOC（该 MOC 本身不计入 active 节点总数）**

#### System 层

- **新建：** `02_Raw/Lectures/Pathology/`（原始讲义目录）与 `02_Raw/Lectures/Pathology/README.md`
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
  - 覆盖：适应 5 种 + 损伤 8 原因机制 + 可逆性变性 7 种 + 细胞死亡 6 亚型 + 凋亡
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
