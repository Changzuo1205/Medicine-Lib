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
4. 课程上下文层（若需要）

> 未创建 MOC 就创建子节点 = 子节点中的 `[[第一章 MOC]]` 引用会未解析，走 Obsidian "未创建"状态。

### 3.2 Frontmatter 模板（强制）

使用以下模板（不要额外加字段，也不要少字段）：

```yaml
---
type: {disease | drug | pathophysiology | symptom | sign | test | procedure | differential | algorithm | case | wrong-answer | flashcard | question | clinical-pearl | moc | course | lecture | navigation}
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

- [ ] 预创 MOC · Discipline README · Source-Registry · Change-Log
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

---

## 8. 使用示例

### 示例：`/ingest 病理学 第一章 组织细胞适应与损伤`

```
Pre-flight（10 分钟）：
  ✓ 提取 docx → 357 段落
  ✓ 枚举 02_Raw/lectures/Pathology/ → 发现 .docx 已在
  ✓ 枚举 03_Concepts/Pathology/ → 发现 6 个预存节点
  ✓ S-LEC-010 + 1 = S-LEC-011

Extract：
  → 21 个概念节点·1 个 MOC ·1 个 README
  → 划分为 3 组（适应 5 / 可逆损伤 8 / 细胞死亡 9）

Create：
  1. 主代理预创 README + MOC（含 alias）
  2. 启动 3 个 subagent 并行写入 21 个节点（互不重叠列表）
  3. 主代理更新 Source-Registry + Change-Log + Dashboard + Knowledge-Status

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
- [[Source-Registry]] （讲座 / 文献汇总）
- [[Change-Log]] （资料库结构变化日志）
