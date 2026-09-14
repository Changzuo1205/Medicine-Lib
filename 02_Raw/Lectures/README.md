---
type: navigation
status: active
last_updated: 2026-09-09
tags:
  - system/navigation
---

# Lectures — 课程/讲座

本目录保存课程/讲座原始资料（PDF / PPTX / 扫描件 / 电子书摘录 / 笔记等），尽量保持原样。

## 组织结构

按**学科（Discipline）**建立子目录，与 `03_Concepts/` 中已注册的学科一一对应：

```text
02_Raw/Lectures/
├── Medical Immunology/        ← 注册学科 1：免疫学
├── Medical Microbiology/      ← 注册学科 2：医学微生物学
├── Human Parasitology/        ← 注册学科 3：人体寄生虫学（待 /ingest）
├── Clinical Epidemiology/     ← 注册学科 4：临床流行病学
└── README.md
```

> 后续注册新学科时，平行建立对应子目录（如 `Pathology/`、`Pharmacology/` 等）。

## 使用规则

- 原始资料不做知识化改写
- 提取的知识写入对应学科目录的 `03_Concepts/<Discipline>/` 节点
- 来源登记到 `99_System/Source-Registry`
- **文件保留原始文件名**（避免引入歧义、保留追溯性）
- 命名规范：`<序号> <章节名>.pdf` 或 `<章节名>.pptx`

## 文件格式转换规则

**当原始文件为 PPT/PPTX 时，自动转换为 PDF 并保留原文件**：

| 格式 | 用途 |
|------|------|
| **PDF（首选）** | Active 文件的引用目标；可视化查看；跨平台稳定 |
| PPTX（保留） | 源文件；可编辑；用于二次修改 |

**实现方式**：通过 Python + Microsoft PowerPoint COM 自动化（`win32com.client`）调用 `Presentations.SaveAs(path, 32)`（`32 = ppSaveAsPDF`）。

**前置条件**：本地需安装 Microsoft PowerPoint 或 LibreOffice。

**自动转换脚本示例**（保存在 `temp/convert_py.py`）：

```python
import win32com.client, pythoncom
pythoncom.CoInitialize()
pp = win32com.client.DispatchEx("PowerPoint.Application")
pp.Visible = 1
pp.DisplayAlerts = 2  # ppAlertsNone
deck = pp.Presentations.Open("<input>.pptx", True, False)
deck.SaveAs("<output>.pdf", 32)  # 32 = ppSaveAsPDF
deck.Close()
pp.Quit()
pythoncom.CoUninitialize()
```

## 当前资料（按学科分组）

### Medical Immunology — 1 份

| 文件 | 章节 | 类型 |
|------|------|------|
| `第一章 免疫学概述.pdf` | 第 1 章 免疫学概述 | PDF |

- 来源登记：`S-LEC-004`
- 关联学科：`[[03_Concepts/Immunology|Immunology]]`
- 关联课程：`[[08_Courses/Medical Immunology/Course|Medical Immunology Course]]`

### Medical Microbiology — 2 份

| 文件 | 章节 | 类型 |
|------|------|------|
| `1 绪论.pdf` | 绪论 | PDF |
| `1 2 第1章 细菌的形态与结构 1.pdf` | 第 1 章 细菌的形态与结构 | PDF |

- 来源登记：`S-LEC-005`（绪论）· `S-LEC-006`（细菌形态与结构）
- 关联学科：`[[03_Concepts/Medical Microbiology|Medical Microbiology]]`
- 关联课程：`[[08_Courses/Medical Microbiology/Course|Medical Microbiology Course]]`

### Clinical Epidemiology — 4 份（2 PPTX + 2 PDF）

| 文件 | 章节 | 类型 |
|------|------|------|
| `流行病学绪论.pptx` | 绪论 | PPTX（原始）|
| `流行病学绪论.pdf` | 绪论 | **PDF（首选参考）**|
| `疾病的分布.pptx` | 疾病的分布 | PPTX（原始）|
| `疾病的分布.pdf` | 疾病的分布 | **PDF（首选参考）**|

- 来源登记：`S-LEC-007`（绪论）· `S-LEC-008`（疾病的分布）
- 关联学科：`[[03_Concepts/Clinical Epidemiology|Clinical Epidemiology]]`（17 节点）
- 关联课程：`[[08_Courses/Clinical Epidemiology/Course|Clinical Epidemiology Course]]`
- 引用约定：Active 文件统一指向 **PDF 版本**；PPTX 保留供编辑

### Human Parasitology — 2 份（1 PPT + 1 PDF）

| 文件 | 章节 | 类型 |
|------|------|------|
| `第一讲 寄生虫学总论2026秋 28号字(1).ppt` | 第 1 讲 寄生虫学总论 | PPT（原始）|
| `第一讲 寄生虫学总论2026秋 28号字(1).pdf` | 第 1 讲 寄生虫学总论 | **PDF（首选参考）** |

- 来源登记：`S-LEC-009`（寄生虫学总论）
- 关联学科：`[[03_Concepts/Human Parasitology|Human Parasitology]]`（11 节点）
- 关联课程：`[[08_Courses/Human Parasitology/Course|Human Parasitology Course]]`
- 引用约定：Active 文件统一指向 **PDF 版本**；PPT 保留供编辑

## 文件整理历史

- **2026-09-09**：从扁平结构重组为按学科的子目录结构（4 个学科）
  - 旧路径 `02_Raw/Lectures/<file>` → 新路径 `02_Raw/Lectures/<Discipline>/<file>`
  - 所有 Concept 节点 / Course / Lecture 文件的引用路径已同步更新

## 待办

- [ ] 提供临床流行病学后续章节（横断面研究、病例对照、队列研究、RCT、诊断试验评价、治疗评价、预后研究、系统综述深入、EBM 深入等）

- [ ] 是否将基础学科（循环 / 泌尿 / 消化）作为新学科注册？
