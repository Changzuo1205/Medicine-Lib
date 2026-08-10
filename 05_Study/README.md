---
type: navigation
status: active
tags:
  - system/navigation
---

# 05_Study — Learning Artifacts（学习产物）

存放学习产物：练习题、错题、闪卡、复习调度。

## 子目录

- [[Questions]] — 练习题
- [[Wrong-Answers]] — 错题
- [[Flashcards]] — 闪卡
- [[Review]] — 跨课程复习调度队列

## 职责边界

| 层 | 目录 | 职责 |
|----|------|------|
| 长期医学知识 | [[03_Concepts/README|03_Concepts]] | 医学知识本体（单一事实源） |
| 课程上下文 | [[08_Courses/README|08_Courses]] | Course / Lecture / Exam Topic / Review Session |
| 学习产物 | 05_Study/ | 题目 / 错题 / 闪卡 / 复习调度 |

## Review 的分工

- `05_Study/Review/` — 跨课程复习调度 / 待复习项目（该做什么）
- `08_Courses/<Course>/Reviews/` — 一次实际复习会话的历史记录（做了什么）

## 使用规则

- 题目优先基于知识库已有内容生成，不超出知识库范围的医学事实
- 错题记录 Why I Was Wrong（错误认知）
- 反复答错的知识点标记为 Knowledge Gap，加入 [[Review]]
- 题目 / 错题 / 闪卡通过 frontmatter `course:` 字段关联课程
