---
type: navigation
status: active
tags:
  - system/navigation
---

# Review — 复习调度（跨课程队列）

本目录存放**跨课程复习调度队列**（该复习什么、下次何时），**不存放**复习会话记录。

- 模板：[[99_System/Templates/19_Review-Session|19_Review-Session]]
- 结构规范：见 [[AGENTS.md]]

## 分层分工（2026-09-14 明确）

| 层 | 位置 | 职责 |
|----|------|------|
| **调度** | 本目录 `05_Study/Review/` | 跨课程复习队列：哪些知识点该复习、下次什么时候（**该做什么**） |
| **记录** | `08_Courses/<Course>/Reviews/` | 一次实际复习会话的完整记录（**做了什么**） |

> 起因：本 README 原写「本目录存放复习会话记录」，与 [[05_Study/README|05_Study/README]] 及 [[08_Courses/README|08_Courses/README]] 的口径冲突。
> 现统一按后两者执行；`Session-2026-09-07-Immunology-Overview` 已移至
> [[08_Courses/Medical Immunology/Reviews/Session-2026-09-07-Immunology-Overview|Medical Immunology/Reviews/]]。

## 当前复习队列

_（暂无登记 — 由 `/review` 生成；知识缺口见 [[99_System/Knowledge-Status|Knowledge Status]]）_

## 复习调度原则（初步建议）

- **新学习**：当天 + 1 天后 + 3 天后 + 7 天后 + 14 天后 + 30 天后（间隔重复）
- **错题**：答错后当天重做 → 3 天后 → 7 天后
- **Lecture 节点**：完成 `/study` 后按上述时间表复习
- **Review Session 记录**：写入 `08_Courses/<Course>/Reviews/`，每次复习后追加条目并更新"自测结果"与"知识缺口"
