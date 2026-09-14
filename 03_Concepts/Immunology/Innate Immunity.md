---
type: physiology
status: active
specialties:
  - Immunology
  - Infectious Disease
tags:
  - medicine/physiology
  - medicine/immunology
  - system/immune
  - medicine/innate-immunity
evidence_level: C
source_status: needs_review
last_reviewed: 2026-09-07
---

# Innate Immunity（固有免疫）

## Definition

固有免疫（innate immunity），又称先天性 / 非特异性免疫，是生物在长期进化过程中逐渐形成的、机体抵御病原体入侵的**第一道防线**。

由**模式识别受体（PRR）**识别病原体相关分子模式（PAMP）和危险相关分子模式（DAMP），无需抗原预先致敏，效应在数分钟至 4 天内启动。

> [!info] 来源
> - 主来源：[[02_Raw/Lectures/Medical Immunology/第一章 免疫学概述.pdf|《免疫学概述》（杨艳艳，2026 秋）]] — 第二节、第四节
> - 来源登记：[[Source-Registry#S-LEC-004]]
> - evidence_level: C（医学教材 / 课程资料）；source_status: needs_review

## Normal Mechanism

### 一、获得形式与时相

| 维度 | 固有免疫 |
|------|----------|
| 获得形式 | 固有性 / 先天性 |
| 抗原参与 | **无需抗原激发** |
| 发挥作用时相 | 早期，快速（**数分钟至 4 天**） |
| 抗原识别受体 | **模式识别受体（PRR）** |
| 免疫记忆 | **无** |

### 二、参与成分

#### 1. 体液因子
- 抑菌、杀菌物质（如溶菌酶）
- **补体**
- 炎症因子（细胞因子、趋化因子）

#### 2. 固有免疫细胞

| 细胞 | 关键特征 |
|------|----------|
| **中性粒细胞** | "野战部队"；外周血 WBC 60–70%；存活 2–3 天；表达趋化因子受体（IL-8R、C5aR）、PRR、调理性受体；可穿越血管内皮进入感染部位 |
| **嗜酸性粒细胞** | 5–6%；组织中数量 > 外周血；分布于呼吸道、消化道、泌尿生殖道黏膜；参与**抗寄生虫免疫** |
| **嗜碱性粒细胞** | 0.2%；外周血中最少；表达补体受体 + IgE Fc 受体（FcεRI）；趋化作用；参与 **I 型超敏反应** |
| **单核/巨噬细胞** | 单核细胞 3–8%；血液停留 12–24h 后迁移全身分化为 Mφ；可分化为 **M1（促炎）/ M2（抗炎）** 亚群 |
| **Mφ 表面受体** | PRR（MR 甘露糖受体、SR 清道夫受体、TLR）；调理性受体（IgG FcR、CR）；趋化与活化受体（MCP-1R、MIP-1α/βR、IFN-γR）；抗原加工提呈相关（MHC I/II、CD80/86 即 B7、CD40） |
| **树突状细胞（DC）** | **最重要的专职 APC**；cDC 来自髓样干细胞；胞饮、调理吞噬、受体内吞；表达 MHC I/II、CD80/86；唯一能高效活化初始 T 细胞的 APC |
| **NK 细胞** | CD3⁻ CD19⁻ CD56⁺ CD16⁺，胞内转录因子 E4BP4⁺；分布：血液、外周淋巴组织、肝、脾等；表达 IgG Fc 受体（FcγRⅢA/CD16）→ **ADCC 效应**；分泌 IFN-γ 为主的 Th1 型细胞因子 |
| **肥大细胞** | 参与 I 型超敏反应；表达 FcεRI |

> [!warning] 占比数值的口径（2026-09-14）
> 中性粒 60–70%、嗜酸性 5–6%、嗜碱性 0.2%、单核 3–8% **均照录自讲义 PPT p50–p52**（原文即写作占比，未给判定界值）。
> 这些是**典型占比**，**不是临床判定阈值** —— `Q-Imm-08` 曾将其当作参考范围使用，已在该题中标注修正。

#### 3. 非经典固有免疫细胞（ILC 家族）
- **固有淋巴样细胞（ILCs）**：ILC1、ILC2、ILC3
- **自然杀伤细胞（NK）**：见上
- **固有样淋巴细胞**：B1 细胞、γδT 细胞（部分归类）

### 三、识别机制

- **模式识别受体（PRR）**：识别病原体相关分子模式（PAMP）或损伤相关分子模式（DAMP）
  - 代表家族：TLR、CLR、RLR、NLR
- **调理性受体**：识别被抗体或补体调理的病原体
  - IgG FcR、补体受体（CR）

### 四、主要生物学功能

| 功能 | 机制 |
|------|------|
| 吞噬杀伤病原体 | 中性粒细胞、Mφ 吞噬 |
| 杀伤胞内寄生菌、肿瘤细胞 | Mφ、NK（ADCC、释放穿孔素/颗粒酶、分泌 IFN-γ） |
| 参与炎症反应 | 释放炎症因子、趋化因子 |
| 加工提呈抗原启动适应性免疫 | Mφ、DC（特别是 DC） |

## Key Components / Steps

```
固有免疫
├── 识别：PRR（识别 PAMP / DAMP）
├── 屏障：皮肤、黏膜、黏液、纤毛、分泌型 IgA
├── 体液因子：溶菌酶、补体、急性时相蛋白、炎症因子
├── 细胞：
│   ├── 吞噬细胞（中性粒细胞、Mφ、DC）
│   ├── 杀伤细胞（NK、γδT）
│   └── 释放炎症介质（肥大细胞、嗜碱性粒细胞、嗜酸性粒细胞）
└── 效应：清除病原体、启动炎症、桥接适应性免疫（抗原提呈）
```

## Physiological Significance

- **速度优势**：分钟级启动，是抗感染的第一道防线。
- **抗原提呈桥梁**：DC 等专职 APC 把"非己"信号提交给 T 细胞，**启动适应性免疫**。
- 适应性免疫应答的**先决条件**。

## Clinical Relevance

- **TLR 激动剂**被开发为疫苗佐剂（如 AS04 = MPL + 氢氧化铝，激活 TLR4）。
- **C5a / C5aR 拮抗**用于补体介导疾病。
- **CAR-NK**、NK 细胞免疫治疗用于肿瘤。
- **粒细胞缺乏**（化疗、放疗、骨髓衰竭）→ 细菌 / 真菌感染风险显著升高，提示固有免疫的临床地位。
- **慢性肉芽肿病（CGD）**：NADPH 氧化酶缺陷 → 吞噬细胞杀菌障碍 → 反复细菌真菌感染 → 印证 Mφ 在固有免疫中的核心地位。

## Related Concepts

- [[Immune System]]
- [[Adaptive Immunity]]
- [[Immune Dysregulation]]
- [[Pattern Recognition Receptor]]（待建）
- [[Complement System]]（待建）
- [[Macrophage]]（待建）
- [[Neutrophil]]（待建）
- [[NK Cell]]（待建）
- [[Dendritic Cell]]（待建）
- [[Hypersensitivity]]（待建，I 型超敏反应）
- [[ADCC]]（待建）

## Sources

- [[02_Raw/Lectures/Medical Immunology/第一章 免疫学概述.pdf|《免疫学概述》（杨艳艳，2026 秋）]] — 第二节、第四节
- 来源登记：[[Source-Registry#S-LEC-004]]
- evidence_level: C
- source_status: needs_review（细胞亚群比例、趋化因子时间窗等需对照标准教材核对）
