---
type: navigation
status: active
last_updated: 2026-09-09
tags:
  - system/navigation
---

# Textbooks — 教材

本目录保存教材原始资料（PDF、扫描件、电子书摘录、笔记等），尽量保持原样。教材作为**长期参考资料源**（Reference / Evidence Source），不直接作为 Concept 来源。

## 组织结构

按**学科（Discipline）**建立子目录，与 `03_Concepts/` 中已注册学科一一对应：

```text
02_Raw/Textbooks/
├── Medical Microbiology/       ← 医学微生物学
├── Medical Immunology/         ← 医学免疫学
├── Human Parasitology/         ← 人体寄生虫学（空，待补充）
├── Clinical Epidemiology/      ← 临床流行病学
├── Pathology/                   ← 病理学
└── README.md
```

> 后续注册新学科时，平行建立对应子目录。

## 使用规则

- 原始资料不做知识化改写
- 提取的知识写入对应学科目录的 `03_Concepts/<Discipline>/` 节点
- 来源登记到 `99_System/Source-Registry`
- **教材 ≠ 老师讲授**：仅作为参考资料；/ingest 需等课程 PPT
- **教材 ≠ 课程笔记**：不直接作为 Concept 来源
- **未知不猜测**：元信息（出版年份/ISBN 等）无法从文件确认时，如实留空

> 完整流程参见 `[[99_System/Textbook-Import-SOP|Textbook-Import-SOP]]`。

## 当前资料（按学科分组）

### Pathology — 1 份（已注册 Reference Source）

| 文件 | 状态 |
|------|------|
| `[[Pathology/README\|《病理学（第10版）》.pdf]]` | ✅ **已注册**（reference-only） |

### Medical Microbiology — 1 份

| 文件 | 章节 / 主编 | 状态 |
|------|-------------|------|
| `11.医学微生物学.pdf` | 待登记 | ⏸ 物理整理完成，**未注册** Reference Source |

### Medical Immunology — 1 份

| 文件 | 章节 / 主编 | 状态 |
|------|-------------|------|
| `免疫系统与疾病.pdf` | 待登记 | ⏸ 物理整理完成，**未注册** Reference Source |

### Clinical Epidemiology — 1 份

| 文件 | 章节 / 主编 | 状态 |
|------|-------------|------|
| `流行病学9版教材.pdf` | 待登记 | ⏸ 物理整理完成，**未注册** Reference Source |

### Human Parasitology — 0 份

_（暂无 — 待用户后续补充）_

## 待办

- [ ] 为 3 本新教材（医学微生物学 / 免疫系统与疾病 / 流行病学 9 版）建立 Reference Source README（按 `[[99_System/Textbook-Import-SOP|SOP]]` 流程）
- [ ] 提供人体寄生虫学教材
- [ ] 是否将基础学科（循环 / 泌尿 / 消化）教材作为新学科注册？
