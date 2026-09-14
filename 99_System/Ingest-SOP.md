---
type: sop
status: active
tags:
  - system/sop
  - system/ingest
created: 2026-09-11
last_updated: 2026-09-11
supersedes: AGENTS.md §19 — /ingest（仅高层概述）
related:
  - AGENTS.md §21 — /audit
  - 99_System/Textbook-Import-SOP.md — Reference Source 注册
---

# /ingest 作业流程 SOP

> 本 SOP 是 AGENTS.md §19 "/ingest" 的详细扩充。AGENTS.md 提供高层概述（八步流程图）；本 SOP 提供可执行的详细检查清单与防护措施。

---

## 0. 三条黄金规则（动手前必读）

1. **不发明医学事实** — 所有内容来源于讲义/教材/指南，不是"模型认为"。
2. **不隐匿不确定性** — 讲义未涉及的机制或临床意义要明确标注（例：`讲义未详述` / `evidence_level: C, source_status: needs_review`）。
3. **不覆盖高价值内容** — 修改既有节点时保留、修补、加链接，不为"格式统一"重写。

> **课件来源的完整产出清单（2026-09-14 起）**：① 章节 MOC　② 概念子节点　③ 跨文件双向链接　④ **课程上下文层 Course + Lecture（§3.5，强制）**　⑤ Source-Registry　⑥ Change-Log　⑦ Dashboard / Knowledge-Status 回写
> **缺任何一项 = 本次 /ingest 未完成**，不得交付。

---

## 1. 预检阶段（Pre-flight）— 动手前 10 分钟

> **原则：记住"你不能修复你不知道存在的错误"。**

### 1.1 资料清点

- [ ] 确认原始文件存在与路径（可以是 .pdf / .pptx / .docx / .md / .txt / .html）
- [ ] **提取原文本**（参见《原文本提取》附录）
- [ ] 查阅原始文件顶部·身份信息（课程名 / 讲者 / 日期 / 版本）
- [ ] 记录源头：`S-LEC-NNN` 讲座 ID（先查 [[99_System/Source-Registry|Source-Registry]] 最大号 + 1）

### 1.2 现状调查

- [ ] **枚举目标学科目录**：
  ```powershell
  Get-ChildItem -Path "<target_dir>" -Force | Select-Object Name, PSIsContainer
  ```
  > 重点：不要只看一级目录，要枚举包含预存文件的子目录。**调查未枚举的目录 = 许多纵向冲突的根源**。
- [ ] **检查预存节点**：如果同名文件已存在，优先"更新"而非"创建"；记入"预存节点名单"供后续对照。
- [ ] 查阅同类子目录的先验节点（如 [[03_Concepts/Immunology/README]] / [[03_Concepts/Medical Microbiology/README]]），了解布局习惯。
- [ ] **枚举课程上下文层** `08_Courses/<Discipline>/`：`Course.md` 是否存在？`Lectures/` 已有哪几讲？
      → 本项直接决定 §3.5 的动作是"新建 Course + Lecture"还是"更新既有 Lecture"。

### 1.3 输出：预存节点名单 + 资源汇总

如果发现预存节点，在继续之前向用户报告"已有 X 个节点与本次 ingest 重叠"，提出合并/覆盖/跳过选项。

---

## 2. 概念提取阶段（Extract）

### 2.1 列出本章概念谱（必须可追溯至原文本段落号）

对于医学概念节点，使用以下模板列表：

```markdown
| 节点名（英中双语） | type | 原文本段落号 | 来源可靠度（A-E） |
|------|------|--------|------|
| Atrophy 萎缩 | pathophysiology | [057]-[076] | C |
```

### 2.2 每个概念的记录要素

1. **中英文名**（双语）
2. **type**：从 [[99_System/Templates/|Templates/]] 选择合适的节点类型（disease / drug / pathophysiology / ...）
3. **原文本段落号**（例：[056]-[076]）—为后续核实提供可追溯性
4. **来源可靠度**（A-E / unknown）
5. **与其他节点的关系**（同类 / 上下位 / 不属于问题）

### 2.3 抵御诱惑："为什么不多创建亚型节点？"

如果讲义提到了"亚型"（例：偏振光下的苹果绿），**不要为这个亚型单独创建节点**，应作为"特征事项"写在上层节点中。例外：如果该亚型在多个独立课题中重复出现或临床意义独立，才独立创建。

---

## 3. 写作阶段（Create / Update）

### 3.1 顺序（关键）

1. **MOC 与 Discipline README 优先** — 为子节点提供入口与别名
2. 子节点依次创建 / 更新
3. 跨文件链接 / 双向链接
4. **课程上下文层同步（课件来源强制）** — 见 §3.5

> 未创建 MOC 就创建子节点 = 子节点中的 `[[第一章 MOC]]` 引用会未解析，走 Obsidian "未创建"状态。
> **顺序不可颠倒**：先 MOC → 再子节点 → 再链接 → 最后课程层。课程层要引用已存在的节点，否则链接悬空。

### 3.2 Frontmatter 模板（强制）

使用以下模板（不要额外加字段，也不要少字段）：

```yaml
---
type: {disease | drug | physiology | pathophysiology | symptom | sign | test | procedure | differential | algorithm | case | question | flashcard | wrong_answer | clinical_pearl | moc | course | lecture | exam_topic | review_session | reference_source | processing_record | navigation | system | sop | dashboard}
> **类型名拼写规则（2026-09-14 定案）**：`type` 一律用**下划线**（`wrong_answer`、`clinical_pearl`、`exam_topic`、`review_session`），
> **不用连字符**。理由：`99_System/Templates/` 下既有模板已全部使用下划线，而旧版本 SOP 写的是连字符 —— 两种拼写会让筛选器漏项。
> 本枚举已补齐此前遗漏的 `physiology`（AGENTS.md §5 允许）、`review_session`、`exam_topic`、`reference_source`、`processing_record`。

status: active | archived
specialties:        # 仅医学节点需要；跨学科的节点列多个
  - Pathology
tags:               # 必须包含以下三类（调整顺序）
  - medicine/pathology            # 学科标签（必填）
  - medicine/pathophysiology      # 类型标签（必填）
  - medicine/cellular-adaptation  # 亚类别标签（选填，依节点分类考虑）
evidence_level: A | B | C | D | | unknown
source_status: verified | needs_review | conflicting | outdated | unsourced
last_reviewed: YYYY-MM-DD
---
```

### 3.3 写作安全规则（关键！本次会话的最大教训）

| 风险 | 防范措施 |
|------|----------|
| **Unicode 转义不可靠**：`\\u82ac` (苬) 被误用为 `\\u51ac` (冬) | 如果使用 `\uXXXX` 转义，写入前先调用 `unicodedata.name()` 验证其 Unicode 名称与意望一致 |
| **中英混排**：`天ast氨酸` | 中文词里不出现 ASCII 字母（学科代号 / 药品缩写除外） |
| **同字似字**：`弎` (三) vs `凋亡` (凋亡) | 写入后跳出 `醯` 、`嗜`/`噬`/`皱` 等夾变字点名，依靠 `unicodedata.name()` 列表核对 |
| **错位代号**：未创建 MOC 就写了 `[[第一章 MOC]]` | 先创 MOC 不设别名，子节点用完整文件名引用；后续重写 MOC 加入 alias |
| **路径偏移**：`../../` 本意是 `课程···` 但实际需 `···` | 写入后途中必须调用 `os.path.normpath` 验证路径存在性；或使用 `[[节点名]]` 纯基名引用（优先） |

### 3.4 优先纯基名引用（推荐）

| 场景 | 推荐写法 |
|------|----------|
| 子节点 ↔ 同一学科其他节点 | `[[Atrophy]]` · `[[Hypertrophy]]` |
| 子节点 ↔ MOC | `[[Chapter 1 - Cellular Adaptation and Injury]]` |
| 子节点 ↔ 不同学科节点 | `[[../Immunology/Immune Dysregulation]]`（相对路径） |
| 子节点 ↔ Source / System | `[[../../../02_Raw/Lectures/Pathology/...]]` · `[[../../../99_System/Source-Registry#S-LEC-011]]` |

> **优先纯基名引用** = 减少路径错误、快捷、与跨平台兼容。

---

### 3.5 课程上下文层同步（强制 — 课件来源必做）

> **规则（2026-09-14 起）**：`/ingest` 的来源若是**课程课件**（讲义 / 慕课笔记 / 课堂笔记，登记为 `S-LEC-NNN`），
> **必须在同一次作业中同步创建该课程的对应章节 Lecture**，不得留待事后补做。
>
> **起因**：病理学第二章 `/ingest` 时，§3.1 原第 4 项写作"课程上下文层（若需要）"，Lecture 被当作可选项跳过，
> 导致 `08_Courses/Pathology/Lectures/` 与知识层脱节，事后由用户发现并要求补齐。该"若需要"的措辞已删除。

#### 3.5.1 判定：什么来源要建 Lecture

| 来源类型 | 编号 | 是否必须建 Lecture |
|----------|------|-------------------|
| 课程课件（讲义 / 慕课笔记 / 课堂笔记） | `S-LEC-NNN` | ✅ **强制** |
| 教材（Reference Source） | `S-TXT-NNN` | ❌ 不建 —— 教材不是"讲授"，见 [[Textbook-Import-SOP]] |
| 指南 / 文献 / 其他 | `S-GDL-*` / `S-PAP-*` | ❌ 不建（除非确为某课程的指定讲授材料） |

#### 3.5.2 必产三件套

1. **`08_Courses/<Discipline>/Course.md`** — 若不存在则新建（课程元信息 + Lectures 清单 + 节点分布 + Source）
2. **`08_Courses/<Discipline>/Lectures/<NN> <中文章节名>.md`** — 本次章节的 Lecture 对象
3. **回写 `Course.md`** — `## Lectures` 清单追加本讲；同步更新 `## Related Medical Knowledge` 的节点计数与 `## Knowledge Gaps`

#### 3.5.3 命名规范（强制）

- 文件名：`<两位数章节号> <中文章节名>.md`，例 `02 损伤的修复.md`、`01 组织细胞适应与损伤.md`
- `Course.md` 中的引用必须与文件名逐字一致：`[[Lectures/02 损伤的修复|02 损伤的修复]]`
- frontmatter `chapter:` 用**阿拉伯数字**（`chapter: 2`），不要写"第二章"

#### 3.5.4 Lecture 必含部分（缺一即 §5.1.7 不通过）

| 部分 | 内容要求 |
|------|----------|
| frontmatter | `type: lecture` · `status` · `course: "[[../Course]]"` · `chapter` · `date` · `instructor` · `topics[]` |
| `> [!info] 来源` callout | 原始资料 wikilink · 讲者 · `[[Source-Registry#S-LEC-NNN]]` · `source_status` · 关联学科 |
| `## Lecture Overview` | 本讲在课程中的位置与主线 |
| `## 章节目标` | 掌握 / 熟悉 / 了解 三层。**讲义未标注掌握程度时必须按 AGENTS.md §26 显式标注为 inference** |
| 各节正文 | 与讲义结构对应；逐节 `> 详见 [[<章节 MOC>#<小节>]]` + 概念节点链接 |
| `## Class Notes` | `源文本特点` / `我的疑问` / `AI 补充（必须核实来源）` 三个 callout |
| `## Related Medical Knowledge` | 指向本章 MOC 与该章全部概念节点 |
| `## Related Questions` | 无题时写 `_（暂无；后续 /quiz 阶段生成）_` |

#### 3.5.5 双向链接（强制）

- Lecture → 章节 MOC；**章节 MOC → Lecture**（写在 MOC 的"相关学科 / 章节"或 `## /ingest 完成状态` 段落）
- Lecture → 概念节点；概念节点**不必**回链 Lecture（避免噪音），但必须能从 MOC 到达 Lecture

#### 3.5.6 例外

- 同一章节**二次 /ingest**（补充或修订）时**更新**已有 Lecture，不新建重复文件
- 若该学科尚无 Course，**先建 Course 再建 Lecture**，不要只建 Lecture 造成孤儿节点
- 讲义**无显式节标题**时照实说明划分依据，**不得伪造节标题**（参见 §7 陷阱表）

---

## 4. 源登记阶段（Record Sources）

- [ ] **主代理**：主 agent 负责 Source-Registry，输出结构如下：
  ```
  | S-LEC-011 | Pathology Chapter 1 — Cellular Adaptation and Injury（组织细胞适应与损伤） | 优课联盟 UOOC（2026 秋） | 2026 秋 | needs_review |
  ```
- [ ] **位置**：`99_System/Source-Registry.md` —讲座表的末尾
- [ ] **编号规则**：按完整顺序续编号（不要跳号）
- [ ] 中文名称包括：课程 / 讲座 · 讲者 / 来源 · 学期 · 状态

---

## 5. 后验阶段（Post-write Verification）— 完成后 5 分钟

> **不跳过本阶段 = 不可代价的错误会贯穿全程。**

### 5.1 必检项（不通过则不允许推送/交付）

- [ ] **5.1.1 路径解析**：所有 `[[...]]` 引用在当前 vault 中可解析（发起人：main）
  ```python
  for m in WIKILINK.finditer(text):
      raw = m.group(1)
      if raw.startswith("../"):
          norm = os.path.normpath(os.path.join(file_dir, raw))
          assert os.path.exists(norm + ".md") or os.path.exists(norm), f"Broken: [[{raw}]]"
  ```
- [ ] **5.1.2 错别字扫描**：以下字符在中文语境出现时为错别字（各项字体在 27 个 Pathology 文件中出现出现 0 次）：
  `弎 芃 鱼 烉 芯 腫 癣 豤 能能 嗠 拑 噥 嗰 盒 喰 乲 蔓`
  → 任一出现 = 走错 Unicode 码点 = 立即修正
- [ ] **5.1.3 Frontmatter 一致性**：所有同类型节点的 frontmatter 字段名与顺序一致
- [ ] **5.1.4 底类型子节点的 type 与其 frontmatter 一致**（例：`Cell Death` 节点在 `Atrophy.md` 里会不会错点为另一个节点）
- [ ] **5.1.5 Source-Registry**：新增讲座在表中，中文不为 `??` / `\ufffd` 等代字体
- [ ] **5.1.6 Change-Log**：本次入库记录已写入 99_System/Change-Log.md
- [ ] **5.1.7 课程上下文层已同步**（课件来源必检，见 §3.5）：`08_Courses/<Discipline>/Course.md` 存在；`Lectures/<NN> <章节名>.md` 已建或已更新；`Course.md` 的 Lectures 清单与节点计数已回写；Lecture ↔ 章节 MOC 双向链接可解析。
      **未通过 = 不得交付**（此项为 2026-09-14 新增，源于病理学第二章 Lecture 漏建事故）

- [ ] **5.1.8 导航页与目录实际一致**（2026-09-14 新增，源于「暂无」占位符腐烂事故）
      逐项核对，任一不符即修复后再交付：
  - Discipline `README.md` 的「已建节点」段：占位符 `_（暂无）_` 是否仍在？节点是否**逐个 wikilink 列出，或经章节 MOC 可到达**？（两种均可）
  - Discipline `README.md` 的「待建节点」清单：**本次已建出的节点必须从中删除**（否则会误导下一轮 /ingest 重复建节点，见 AGENTS.md §11）
  - 各章节 MOC 的**分组标题数字**是否等于其表格实际行数？（例：`二、可逆性损伤 — 7 个节点` 而表内 8 行 = 不通过）
  - MOC 末的**总数算式**是否自洽？（例：`21 个（适应 5 + 可逆损伤 8 + 细胞死亡 9）` → 5+8+9=22 ≠ 21 = 不通过）
  - `AGENTS.md` §4 注册学科节点数、`07_MOCs/Medicine MOC.md`、`00_Dashboard/Home.md`、`99_System/Knowledge-Status.md` 的节点数是否同步？
  - 布局类 README（`08_Courses/README.md`、`03_Concepts/Diseases/README.md` 等）中「暂不创建 / 暂无」一类陈述是否已被事实推翻？
- [ ] **5.1.9 陈旧「（待建）」标记扫描**（2026-09-14 新增）
      扫描本次涉及的学科目录与 MOC，凡形如 `[[X]]（待建）` 而 `X.md` **已存在**者，一律删除该标记。
      > 原因：同批 /ingest 内节点互相标注「待建」，批次结束后不会自动失效，连续多批后成片失真。
      ```python
      # 检出：wikilink 后 12 字符内出现「（待建」但目标文件存在
      LINK = re.compile(r'\[\[([^\]|#]+)(?:\|[^\]]*)?\]\][^\n\[]{0,12}?（待建')
      ```
- [ ] **5.1.10 归档层 status 一致性**（2026-09-14 新增）
      `99_System/Archive/` 下的文件 `status` 必须是 `archived`，**不得为 `active`**；
      活跃层文件不得为 `archived`。移入 Archive 时必须同批改 `status`。
      ```powershell
      # 检出：归档目录下仍标 active 的文件
      Get-ChildItem 99_System/Archive -Recurse -Filter *.md |
        Select-String -Pattern '^status:\s*active' -List
      ```
- [ ] **5.1.11 `specialties` 取值合法**（2026-09-14 新增）
      每个取值必须是下列之一，否则视为拼写漂移：
      ① `06_Specialties/` 下**已存在**的目录名（临床专科）；
      ② `03_Concepts/` 下**已注册的学科名**（基础/方法学学科，如 `Pathology`、`Immunology`）；
      ③ `03_Concepts/README` 「specialties 允许值」表中显式列出的其他应用方向（如 `Tropical Medicine`、`Public Health and Preventive Medicine`）。
      > 原因：本字段历史上混用了「学科名」与「临床专科名」两套口径，12 个取值中仅 4 个能对应到 `06_Specialties/` 目录，无法机械校验。

### 5.2 建议项（越做越好）

- [ ] 临床重要医学事实在 concept node 中标注 `evidence_level` 与 `source_status`
- [ ] 跨学科联动项在 Knowledge Gaps 区阶明示"待建"
- [ ] Dashboard / Knowledge-Status 更新数据及结构反映

### 5.3 最终报告模板

```
=== /ingest 完成报告 ===

Created：N 个
- · · ·

Updated：M 个
- · · ·

Linked：K 个
- · · ·

Warnings：
- · · ·

Needs Review：
- · · ·
```

---

## 6. 并行 / 多 Agent 协作模式

如果概念过多·要使用 subagent 并行创建，必须严格遵守以下模式：

### 6.1 主代理职责

- [ ] 预创 MOC · Discipline README · Source-Registry · Change-Log · **课程上下文层（Course + Lecture，见 §3.5）**
- [ ] 拆分任务为互不重叠的写入集（例：按"适应 / 可逆伤害 / 细胞死亡" 三组）
- [ ] 为每个 subagent 明确文件名列表 + 模板 + 内容范围
- [ ] **提醒 subagent 创建前先检查预存文件**（防止覆盖）
- [ ] subagent 完成后主代理走 **5.1 后验检查**，中间发现问题代代理修复
- [ ] **不允许 subagent 修改 MOC / README / Source-Registry / Change-Log**

### 6.2 Subagent 职责

- [ ] 严格在分配的文件名列表内创建
- [ ] 不动 MOC / README / Source-Registry / Change-Log / 其他 subagent 分配的文件
- [ ] 不动 原始资料文件
- [ ] Wiki-link 优先使用纯基名引用，必要时使用相对路径 且 在报告中列出未解析链接
- [ ] 输出代理报告：创建了哪些文件 / 行数 / 错误清单

---

## 7. 其他常见陷阱（Pitfalls）

| 陷阱 | 描述 | 解决 |
|------|------|------|
| "三项6"为"三项..." | 中英文重型字符与起始中英文多字符错位 | `天冬氨酸` = 3 个字· `天ast氨酸` = 4 个字· 永远检查总长度 |
| "节点"为"章节" | `第一芃` (·芃 = 芃 = 芃) vs `第一节` (·节 = 节 = 节) | 使用 `节` 不要使用 `芃` |
| "查询某项"未枚举 | 子目录包含预存文件但主代理未检查 | 严格按 1.2 项完成现状调查 |
| MOC 别名未设 | 子节点 `[[第一章 MOC]]` 未解析 | MOC 创建后须加入 `aliases: [Cellular Adaptation and Injury, 第一章]` |
| 路径偏移一级 | `../../` 实际需 `../../../` | 5.1.1 后验中验证所有路径 |
| 多 agent 并行覆盖 | agent 未检查预存文件，导致写入冲突 | 主代理按 6.1 完成资源预检 |
| **Lecture 漏建**（2026-09-14） | §3.1 原写"课程上下文层（若需要）"，措辞使其看起来可选 → 课件 ingest 后 `08_Courses/` 与知识层脱节，事后由用户发现 | 该"若需要"措辞**已删除**；§3.5 改为**强制**，§5.1.7 后验拦截 |
| Lecture 与 MOC 命名不一致 | Lecture 叫 `02 损伤的修复`，MOC 叫 `Chapter 2 - Repair`，双向链接易漏一边 | 双向链接写在固定位置，见 §3.5.5；后验 5.1.1 验证可解析 |
| Lecture `章节目标` 伪装成来源 | 讲义未标注掌握程度，却填了"掌握/熟悉/了解" | 必须加 `> [!info] Clinical Reasoning` 标注（AGENTS.md §26） |

---

## 8. 使用示例

### 示例：`/ingest 病理学 第一章 组织细胞适应与损伤`

```
Pre-flight（10 分钟）：
  ✓ 提取 docx → 357 段落
  ✓ 枚举 02_Raw/Lectures/Pathology/ → 发现 .docx 已在
  ✓ 枚举 03_Concepts/Pathology/ → 发现 6 个预存节点
  ✓ S-LEC-010 + 1 = S-LEC-011

Extract：
  → 21 个概念节点·1 个 MOC ·1 个 README
  → 划分为 3 组（适应 5 / 可逆损伤 8 / 细胞死亡 9）

Create：
  1. 主代理预创 README + MOC（含 alias）
  2. 启动 3 个 subagent 并行写入 21 个节点（互不重叠列表）
  3. 主代理更新 Source-Registry + Change-Log + Dashboard + Knowledge-Status
  4. 主代理同步课程上下文层（§3.5 强制）：Course.md + Lectures/01 组织细胞适应与损伤.md

Post-write：
  1. 路径解析：21 个 wiki-link · 发现 49 个路径偏移 → 主代理修复
  2. 错别字扫描：发现 30+ 变位· 包括 弎→凋亡 · 癣→糜 · 能能→障碍 · · → 主代理重写
  3. Source-Registry 中文验证
  4. Change-Log 已写入

Report：
  Created: 23 / Updated: 0 / Warnings: 2 (需人卫版核实)
```

---

## 9. 参考

- [[AGENTS.md]] § 19 "/ingest"（高层概述）
- [[AGENTS.md]] § 21 "/audit"（完整 audit 流程）
- [[99_System/Textbook-Import-SOP.md]] （Reference Source 注册流程）
- [[99_System/Templates/|Templates/]] （节点模板）
- [[99_System/Templates/17_Lecture|17_Lecture]] （Lecture 模板 —— §3.5.4 必含部分的对应模板）
- [[08_Courses/README|08_Courses]] （课程上下文层职责边界）
- [[Source-Registry]] （讲座 / 文献汇总）
- [[Change-Log]] （资料库结构变化日志）
