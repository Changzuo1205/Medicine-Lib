---
type: navigation
status: active
tags:
  - system/navigation
  - medicine/clinical-epidemiology
  - medicine/epidemiology
  - medicine/evidence-based-medicine
---

# Clinical Epidemiology — 临床流行病学

> **学科全名**：临床流行病学（Clinical Epidemiology）
> **注册日期**：2026-09-09
> **学科层次**：方法学 + 临床医学桥梁（基础医学 → 临床决策证据评估）
> **关联导航**：
> - 专科导航：[[06_Specialties/Public Health and Preventive Medicine|公共与预防医学]]（待建）
> - MOC：[[Clinical Epidemiology MOC]]（待建）
> - 课程：[[../../../08_Courses/Clinical Epidemiology/Course|Clinical Epidemiology Course]]（已建）
> - 已注册学科：[[../Immunology\|Immunology]] · [[../Medical Microbiology\|Medical Microbiology]] · [[../Human Parasitology\|Human Parasitology]] · [[../Pathology\|Pathology]] · **本学科**

## 学科范围

临床流行病学是**流行病学的方法学原理在临床医学中的应用**。本学科涵盖：

### 1. 流行病学基础（Epidemiology Foundations）

- **定义与历史**：流行病学概念、发展史、John Snow 与霍乱调查、中国公共卫生发展
- **疾病分布（Distribution of Disease）**：
  - **人群分布**（年龄、性别、种族、职业）
  - **时间分布**（短期波动、季节性、周期性、长期趋势）
  - **地区分布**（地方性、移民流行病学）
- **疾病频率测量**：
  - **发病率（incidence rate）** vs **患病率（prevalence）**（核心区别）
  - 死亡率（mortality rate）、病死率（case fatality rate）
  - 生存率、累积发病率、发病密度（incidence density）

### 2. 病因与因果推断（Causation & Causal Inference）

- **病因模型**：流行病学三角（宿主-病原-环境）、轮状模型、疾病因素网络
- **因果关系判定**：Hill 标准（强度、一致性、特异性、时序性、生物梯度、生物学合理性、连贯性、实验证据、类比）
- **充分病因 vs 必要病因**

### 3. 研究设计（Study Design）

| 类型 | 典型设计 | 证据等级 |
|------|----------|----------|
| **描述性** | 病例报告、横断面研究、生态学研究 | 低 |
| **分析性（观察）** | 病例对照研究、队列研究（前瞻 / 回顾 / 双向） | 中 |
| **实验性** | 随机对照试验（RCT）、Field Trial、社区试验 | 高 |
| **理论性** | 数学模型、决策分析 | — |

### 4. 偏倚与混杂（Bias & Confounding）

- **选择偏倚**（selection bias）：入院率偏倚、Berkson 偏倚、无应答偏倚
- **信息偏倚**（information bias）：回忆偏倚、调查者偏倚、测量偏倚
- **混杂偏倚**（confounding）：定义、识别、控制方法
- **控制方法**：限制、匹配、随机化、分层分析、标准化、多变量分析（回归模型）

### 5. 诊断试验评价（Diagnostic Test Evaluation）

| 指标 | 含义 | 公式 |
|------|------|------|
| **灵敏度** | 实际有病中筛阳性的比例 | TP / (TP + FN) |
| **特异度** | 实际无病中筛阴性的比例 | TN / (TN + FP) |
| **阳性预测值（PPV）** | 筛阳性中实际有病的比例 | TP / (TP + FP) |
| **阴性预测值（NPV）** | 筛阴性中实际无病的比例 | TN / (TN + FN) |
| **阳性似然比（LR+）** | 灵敏度 / (1 - 特异度) | — |
| **阴性似然比（LR-）** | (1 - 灵敏度) / 特异度 | — |
| **Youden 指数** | 灵敏度 + 特异度 - 1 | — |
| **ROC 曲线 / AUC** | 综合评估诊断价值 | — |

- **贝叶斯定理**：验前概率 → 验后概率（通过似然比调整）

### 6. 治疗效果评价（Therapeutic Evaluation）

- **RCT 设计核心原则**：随机化（randomization）、对照（control）、盲法（blinding）、样本量估计
- **意向治疗分析（ITT）** vs 符合方案分析（PP / per-protocol）
- **效应指标**：
  - **相对风险（RR）** = 暴露组发病率 / 非暴露组发病率
  - **相对风险降低（RRR）** = (1 - RR) × 100%
  - **绝对风险降低（ARR）** = 非暴露组发病率 - 暴露组发病率
  - **NNT（需治数）** = 1 / ARR（治疗 1 例获益所需治疗的患者数）
  - **NNH（需害数）** = 1 / AE 绝对增加（治疗 1 例不良反应所需治疗的患者数）

### 7. 预后研究（Prognosis Research）

- 生存率、5 年生存率、中位生存期
- **Kaplan-Meier 曲线**（生存函数）
- **Cox 比例风险模型**（多因素生存分析）
- **HR（Hazard Ratio）** 解读

### 8. 系统综述与 Meta 分析（Systematic Review & Meta-analysis）

- **PRISMA 声明**（报告规范）
- **异质性评估**：Q 检验、I² 统计量
- **效应模型**：固定效应（fixed-effect）vs 随机效应（random-effect）
- **森林图（forest plot）**解读
- **漏斗图（funnel plot）**与发表偏倚
- **GRADE 证据评级**

### 9. 循证医学（Evidence-Based Medicine, EBM）

- **PICO 框架**（Population / Intervention / Comparison / Outcome）
- **证据等级金字塔**：系统综述/Meta-analysis → RCT → 队列 → 病例对照 → 病例报告 → 专家意见
- **GRADE 系统**：证据质量分级（High / Moderate / Low / Very Low）+ 推荐强度（Strong / Weak）
- **临床实践指南**的形成与评价（AGREE Ⅱ）

### 10. 公共卫生监测与爆发调查（Public Health Surveillance & Outbreak Investigation）

- **监测系统**类型：被动 vs 主动
- **爆发识别**与控制：流行病学调查步骤
- **疫苗效力**（Vaccine Efficacy / Effectiveness）评估

---

## 已建节点（17）

> 2026-09-09 首次 /ingest（来源 `S-LEC-007` 流行病学绪论 + `S-LEC-008` 疾病的分布）。
> 全部 17 个节点 `source_status: needs_review`，待与教材逐句核对。

| 分组 | 节点 |
|------|------|
| 学科本体 | [[Epidemiology]] · [[Clinical Epidemiology (concept)]] · [[History of Epidemiology]] · [[Evidence-Based Medicine]] |
| 疾病分布 | [[Disease Distribution]] · [[Distribution by Population]] · [[Distribution by Time]] · [[Distribution by Place]] · [[Migration Epidemiology]] · [[Epidemic Intensity]] |
| 频率测量 | [[Disease Frequency Measures]] · [[Incidence Rate]] · [[Prevalence]] · [[Mortality Rate]] · [[Case Fatality Rate]] · [[Survival Rate]] |
| 研究方法 | [[Meta-Analysis]] |

## 待建节点（Knowledge Gaps）

### 研究设计（Study Design）

- Cross-Sectional Study（横断面研究）
- Case-Control Study（病例对照研究）
- Cohort Study（队列研究）
- Randomized Controlled Trial（随机对照试验）
- Systematic Review（系统综述）

### 效应指标（Effect Measures）

- Relative Risk（相对风险）· Odds Ratio（比值比）
- Absolute Risk Reduction（绝对风险降低）· NNT · NNH

### 诊断试验（Diagnostic Test）

- Sensitivity（灵敏度）· Specificity（特异度）· PPV · NPV
- Likelihood Ratio（似然比）· ROC 曲线与 AUC

### 偏倚（Bias）

- Selection Bias · Information Bias · Confounding
- Recall Bias · Berkson's Bias · Lead-Time Bias

### 因果推断

- Hill Criteria
- 流行病学三角 · 轮状模型 · 病因网络

### 循证医学工具

- Evidence Pyramid（证据金字塔）· GRADE System · PICO Framework
- PRISMA / CONSORT / STROBE 报告规范

### 算法（Clinical Algorithm）

- 诊断概率计算（贝叶斯更新）
- 治疗决策中的获益 / 风险评估（NNT / NNH）

### 病例（Case）

- 待 /case 生成（侧重「如何读论文 / 评证据」）

> **注**：`[[Clinical Epidemiology MOC]]` 与 `06_Specialties/Public Health and Preventive Medicine` **均未创建** —— 前者为本章导航页缺口，后者为专科目录缺口。

## 学科关系图

```
临床流行病学（Clinical Epidemiology）
├── 流行病学基础（理论）
│   ├── 疾病分布 → 频率指标
│   ├── 病因 → 因果推断标准
│   └── 研究设计 → 选择合适设计
│
├── 方法学核心
│   ├── 偏倚识别与控制
│   ├── 诊断试验评价（Se / Sp / PPV / NPV / LR / ROC）
│   ├── 治疗效果评价（RCT / RR / ARR / NNT）
│   ├── 预后研究（KM / Cox）
│   └── 系统综述 / Meta 分析
│
├── 应用层
│   ├── 临床决策（贝叶斯更新）
│   ├── 临床指南制定（GRADE）
│   └── 公共卫生监测 / 爆发调查
│
└── 工具与产出
    ├── 研究论文（撰写 + 评价）
    ├── 临床指南
    └── 系统综述
```

## 使用规则

1. **本目录定位**：存放**临床流行病学方法学相关**的 Concept 节点（Study Design / Measures / Bias / Causation / EBM / Algorithm）。
2. **与其他学科的关联**：
   - 与 [[03_Concepts/Immunology\|Immunology]] 等学科的交叉在于"研究设计 → 评价该学科的研究证据"
   - 与 [[04_Clinical/Algorithms\|Algorithms]]（04_Clinical）互补：算法是临床决策；本学科是评估算法依据的证据
3. **来源优先**：所有方法学内容以国际公认标准为准（Cochrane Handbook、STROBE、CONSORT、PRISMA、GRADE 等）。
4. **数学 / 公式内容**：指标公式与计算示例可保留；具体疾病数据不在本目录。

## 注册信息

- **注册日期**：2026-09-09
- **注册原因**：用户要求注册"临床流行病学"作为新学科
- **素材位置**：`02_Raw/Lectures/Clinical Epidemiology/流行病学绪论.pdf` + `02_Raw/Lectures/Clinical Epidemiology/疾病的分布.pdf`
- **关联课程**：[[../../../08_Courses/Clinical Epidemiology/Course|Clinical Epidemiology Course]]（已建，2026-09-09）
- **状态**：active（**已建 17 个 Concept 节点**，见上「已建节点」）

## 相关导航

- [[03_Concepts/Immunology/README\|Immunology 学科目录]]
- [[03_Concepts/Medical Microbiology/README\|Medical Microbiology 学科目录]]
- [[03_Concepts/Human Parasitology/README\|Human Parasitology 学科目录]]
- [[Medicine MOC]]
- 06_Specialties 待建：Public Health and Preventive Medicine / Clinical Epidemiology
