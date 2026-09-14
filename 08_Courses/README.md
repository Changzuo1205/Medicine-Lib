---
type: navigation
status: active
tags:
  - system/navigation
---

# 08_Courses — Course Context Layer（课程上下文层）

存放**课程上下文**：Course / Lecture / Exam Topic / Review Session。

课程知识在此层组织，**不写入**长期医学知识层。

## 职责边界

| 层 | 目录 | 职责 |
|----|------|------|
| 长期医学知识 | [[03_Concepts/README|03_Concepts]] | 医学知识本体（单一事实源，被所有课程共享引用） |
| 课程上下文 | 08_Courses/ | 课程结构：Course / Lecture / Exam Topic / Review Session |
| 学习产物 | [[05_Study/README|05_Study]] | 题目 / 错题 / 闪卡 / 复习调度 |

## 本层对象

- [[16_Course|Course]] — 一门课程（课程导航页）
- [[17_Lecture|Lecture]] — 一次讲课（课堂笔记 + 老师强调 + AI 补充）
- [[18_Exam-Topic|Exam Topic]] — 一个考点（考试重点标记）
- [[19_Review-Session|Review Session]] — 一次复习会话记录

## 目录结构

```
08_Courses/
├── README.md
└── <CourseName>/          # 每门课一个目录（英文 slug）
    ├── Course.md          # Course 对象
    ├── Lectures/          # Lecture 对象
    ├── Exams/             # Exam Topic 对象（尚未创建）
    └── Reviews/           # Review Session 对象（尚未创建）
```

### 已建课程（5 门，截至 2026-09-14）

| 课程 | Course | Lectures | 对应学科 |
|------|--------|----------|----------|
| Medical Immunology | [[Medical Immunology/Course\|Course]] | 01 免疫学概述 · 03 抗原 | [[03_Concepts/Immunology/README\|Immunology]] |
| Medical Microbiology | [[Medical Microbiology/Course\|Course]] | 01 绪论 · 02 细菌的形态与结构 | [[03_Concepts/Medical Microbiology/README\|Medical Microbiology]] |
| Human Parasitology | [[Human Parasitology/Course\|Course]] | 01 寄生虫学总论 | [[03_Concepts/Human Parasitology/README\|Human Parasitology]] |
| Clinical Epidemiology | [[Clinical Epidemiology/Course\|Course]] | 01 流行病学绪论 · 02 疾病的分布 | [[03_Concepts/Clinical Epidemiology/README\|Clinical Epidemiology]] |
| Pathology | [[Pathology/Course\|Course]] | 01 组织细胞适应与损伤 · 02 损伤的修复 | [[03_Concepts/Pathology/README\|Pathology]] |

> **已知缺口**：5 门课均未创建 `Exams/` 与 `Reviews/` 子目录；`Medical Immunology` 的 Lecture 编号为 01、03（**缺 02**，该章尚未 /ingest）。

## 使用规则

1. 课程内容只存在于本层；进入 [[03_Concepts/README|03_Concepts]] 必须经过「提炼为通用知识」
2. Lecture / Exam Topic 只通过 wikilink 引用医学节点，不复制内容
3. 老师强调 / 考试重点只在本层标记，不写入医学节点
4. 复习调度见 [[05_Study/README|05_Study/Review]]，复习会话记录在本层 Reviews/
5. **Lecture 由 `/ingest` 同步创建（2026-09-14 起强制）**：课件来源（`S-LEC-NNN`）ingest 时，必须**同批**创建
   `Course.md` 与 `Lectures/<NN> <章节名>.md`，不得事后补做。命名、必含部分与双向链接要求见
   [[99_System/Ingest-SOP|Ingest-SOP]] §3.5；后验对应 §5.1.7。
   > 起因：病理学第二章 ingest 时 Lecture 被当作可选项跳过，造成本层与知识层脱节。
