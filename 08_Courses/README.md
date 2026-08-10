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

## 目录结构（示例，待真实课程表后创建）

```
08_Courses/
├── README.md
└── <CourseName>/          # 每门课一个目录（英文 slug）
    ├── Course.md          # Course 对象
    ├── Lectures/          # Lecture 对象
    ├── Exams/             # Exam Topic 对象
    └── Reviews/           # Review Session 对象
```

> 注意：当前尚未提供真实课程表，暂不创建任何具体课程目录。

## 使用规则

1. 课程内容只存在于本层；进入 [[03_Concepts/README|03_Concepts]] 必须经过「提炼为通用知识」
2. Lecture / Exam Topic 只通过 wikilink 引用医学节点，不复制内容
3. 老师强调 / 考试重点只在本层标记，不写入医学节点
4. 复习调度见 [[05_Study/README|05_Study/Review]]，复习会话记录在本层 Reviews/