---
type: navigation
status: active
tags:
  - system/navigation
---

# 03_Concepts — 核心知识库

存放正式知识节点。每个重要医学概念尽可能建立独立 Markdown 文件。

## 组织原则（V2）

**按学科（Discipline）组织为主，按知识类型（Knowledge Type）为辅。**

> V1（2026-08-10 起）曾使用"按知识类型"目录 `Physiology/` 与 `Pathophysiology/`。该组织方式已在 2026-09-07 废弃，相关节点归档至 [[99_System/Archive/Concepts-Retired/]]。详见 [[Change-Log]] 2026-09-07 第三条。

### 双轴分类

一个医学概念同时具有两个维度：

| 维度 | 标识 | 说明 |
|------|------|------|
| **学科归属** | 文件所在目录 | `[[03_Concepts/Immunology/README\|Immunology]]`、`[[03_Concepts/Cardiology/README\|Cardiology]]` … |
| **知识类型** | `frontmatter.type` | `physiology` / `pathophysiology` / `disease` / `drug` …（决定使用哪个模板） |
| **临床专科 / 应用方向** | `frontmatter.specialties` | 涉及的具体临床方向或应用领域（可多个）——取值白名单见下 |
| **学科标签** | `frontmatter.tags` | 如 `medicine/immunology`（便于查询聚合） |

学科目录下允许混合 `type`（如 Immunology 同时有 `physiology` 与 `pathophysiology` 节点），不再分子目录。

### `specialties` 允许值（2026-09-14 明确）

历史上本字段**混用了两套口径**：基础/方法学学科名（`Pathology`、`Immunology`）与临床专科名（`Nephrology`、`Infectious Disease`）。
12 个取值中只有 4 个能对应到 `06_Specialties/` 下的目录，因此无法机械校验。现明确取值必须是下列之一：

| 类别 | 允许值 | 说明 |
|------|--------|------|
| **临床专科**（`06_Specialties/` 目录） | Cardiology · Respiratory · Gastroenterology · Nephrology · Endocrinology · Neurology · Infectious Disease · Hematology · Oncology · Surgery · Pediatrics · Obstetrics-Gynecology · Psychiatry · Dermatology · Emergency Medicine | 建节点时优先用这些 |
| **已注册学科**（`03_Concepts/`） | Pathology · Immunology · Medical Microbiology · Human Parasitology · Clinical Epidemiology | 基础/方法学学科，**与目录冗余但允许保留** |
| **应用方向**（已建目录） | Tropical Medicine · Public Health and Preventive Medicine · Allergy · Rheumatology | 2026-09-14 补建 `06_Specialties/` 目录，现已可聚合 |
| **非临床方向**（白名单，无目录） | History of Medicine · Evidence-Based Medicine | 学科史 / 方法学，不建临床专科目录 |

> **已处理（2026-09-14）**：原 12 个取值中仅 4 个能对应 `06_Specialties/` 目录。已补建 4 个专科目录
> （`Tropical Medicine` / `Public Health and Preventive Medicine` / `Allergy` / `Rheumatology`，共覆盖 42 个节点引用），**现 8/12 有目录**。
> 余下 4 个：`Pathology`(48)、`Immunology`(16) 属**已注册学科名**（与目录冗余但允许保留）；
> `History of Medicine`(2)、`Evidence-Based Medicine`(1) 属非临床方向，列白名单。
> **仍待人工决定**：是否移除与目录冗余的 `Pathology` / `Immunology` 取值。

## 子目录

### 已注册学科（Disciplines）

- [[Immunology]] — 免疫学（首个 V2 注册学科）

### 跨学科"知识类型"目录（保留）

> 这些目录以"知识类型"为单位，不属于任何具体学科。
> 节点应放在最合适的学科目录下；当概念跨学科且无明确学科目录时，临时放在此。

- [[Diseases]] — 疾病
- [[Drugs]] — 药物
- [[Procedures]] — 操作 / 治疗技术
- [[Symptoms]] — 症状
- [[Signs]] — 体征
- [[Tests]] — 检查

### 退役存档

- [[99_System/Archive/Concepts-Retired/]] — V1 中按知识类型组织的 Physiology / Pathophysiology 节点；注册新学科时可从 Archive 复活

## 使用规则

1. 每个概念一个文件，遵循 [[99_System/Templates|对应模板]]
2. 使用 YAML Frontmatter（type / status / specialties / evidence_level / source_status / last_reviewed）
3. 优先建立双向链接，而非复制内容
4. 不确定的证据标记 `needs_review` / `unsourced`
5. 新建节点前先检查是否已存在同名或近似节点（搜索本目录与所有学科目录）
6. **学科归属优先（V2 新规则）**：新节点必须放在**已注册学科目录**下，或在跨学科"知识类型"目录下。
   - ❌ 禁止新建 `Physiology/` 或 `Pathophysiology/` 目录（V1 已废弃）
   - ❌ 禁止将新节点放入 99_System/Archive/Concepts-Retired/（Archive 不属于活跃知识层）
   - ✅ 若某概念属于某个尚未注册学科，可临时放入"知识类型"目录并在 Knowledge-Status 标记 Knowledge Gap，等该学科注册时再迁入
7. 同一学科目录下允许混合 `type: physiology` 与 `type: pathophysiology` 节点
