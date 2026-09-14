---
type: processing_record
status: archived
source_file: "02_Raw/Lectures/尿的生成与排出-2026-春.pdf"
processed_date: 2026-08-16
archived_from: 01_Inbox
archived_date: 2026-08-20
tags:
  - system/processing
  - golden-sample
---

# Processing Record — 尿的生成与排出

## 原始资料（Course Context Source）
| 项目 | 内容 |
|------|------|
| 文件名 | 尿的生成与排出-2026-春.pdf |
| 位置 | `02_Raw/Lectures/`（原始文件未移动、未修改） |
| 类型 | 课程 PPT / 讲义 |
| 主题 | Formation and Excretion of Urine |
| 讲师 | 石丽敏（青岛大学 qdu.edu.cn，待确认课程归属） |
| 时间标注 | 2026 春 |
| 总页数 | 120 |
| 文件大小 | ≈5.1 MB |
| 课程归属 | 未确认（待用户提供真实课程名） |

## 处理方式

Golden Sample 实验：验证「课程资料 → Lecture → Concept → Quiz」流程。

- 未批量处理 Circulation section3 / section4
- 未修改 AGENTS.md
- 未修改其他已有医学节点（当前仅新增 0 节点基础上的扩展）

## 课件结构（六大 Section）

| Section | 页码范围 | 主题 |
|---------|---------|------|
| Section 1 | p3-33 | Functional anatomy of kidney & Renal blood flow |
| Section 2 | p34-44 | Glomerular Filtration |
| Section 3 | p45-80 | Solute transport of renal tubule and collecting duct |
| Section 4 | p81-82 | Urinary concentration and dilution |
| Section 5 | p83-109 | Regulation of urinary formation |
| Section 6 | p110-116 | Clearance |
| 复习题 | p117-119 | 名词解释 + 问答题 |

## 产出清单

- `[[Lecture-Urine-Formation-2026-Spring]]` — Lecture 对象（暂存 Inbox，待课程名确认后移入 08_Courses/）
- **14 个 Physiology Concept**（`03_Concepts/Physiology/`）：
  - 肾单位 Nephron
  - 球旁器 Juxtaglomerular Apparatus
  - 肾小球滤过膜 Glomerular Filtration Membrane
  - 肾血流量 Renal Blood Flow
  - 肾血流量自身调节 Autoregulation of Renal Blood Flow
  - 肾小球滤过 Glomerular Filtration
  - 肾小球滤过率 GFR
  - 滤过分数 Filtration Fraction
  - 有效滤过压 Effective Filtration Pressure
  - 肾小管重吸收与分泌 Tubular Reabsorption and Secretion
  - 水通道蛋白 Aquaporin
  - 球-管平衡 Glomerulotubular Balance
  - 抗利尿激素 ADH
  - 肾素-血管紧张素-醛固酮系统 RAAS
- **12 个 Question**（`05_Study/Questions/`，`QUr-*` 前缀）
- 更新 `[[Nephrology MOC]]` — 添加 Section 导航链接

## 待办

- [ ] 用户确认课程名 → 将 Lecture 移入 `08_Courses/<Course>/Lectures/` 并创建 Course.md
- [ ] 与教科书核对关键数据（如 GFR=125 ml/min、滤过分数=0.19、肾糖阈=180 mg/100ml、葡萄糖 Tm=300 mg/100ml 等）
- [ ] 人工确认「皮质肾单位入球口径大于出球」vs「无差异」（PPT p12 表格内前后存在轻微表述差异，见 Lecture 笔记"我的疑点"）
- [ ] Section 4「尿液浓缩稀释」在 PPT 中仅 2 页（p81-82），无内容要点，需要补充/查教科书
