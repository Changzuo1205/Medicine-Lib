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

> 由 `/review 寄生虫 蛔虫与鞭虫` 于 **2026-09-21** 首次登记。

| 主题 | 范围 | 上次复习 | 下次复习 | 会话记录 |
|------|------|----------|----------|----------|
| **蛔虫与鞭虫**（医学蠕虫学 第一章 线虫） | Lecture 02 + 9 概念节点 + 13 题（Q-Para-01~13）+ 8 闪卡（FC-Para-01~08） | 2026-09-21（首次） | **2026-09-22**（+1 d） | [[08_Courses/Human Parasitology/Reviews/Session-2026-09-21-Ascaris-Trichuris|Session-2026-09-21-Ascaris-Trichuris]] |

**该主题的后续复习排期**（间隔重复）：2026-09-24（+3 d）→ 2026-09-28（+7 d）→ 2026-10-05（+14 d）→ 2026-10-21（+30 d，与下一讲「钩虫·蛲虫」合并做线虫跨讲综合复习）。

> **等待 `/review` 登记的候选**：医学免疫学第四章 抗体（2026-09-21 `/ingest`，31 节点已建但**尚无复习会话**）· 病理学第三章 局部血液循环障碍（2026-09-18 `/ingest`，21 节点已建但**尚无复习会话**）。

## 复习调度原则（初步建议）

- **新学习**：当天 + 1 天后 + 3 天后 + 7 天后 + 14 天后 + 30 天后（间隔重复）
- **错题**：答错后当天重做 → 3 天后 → 7 天后
- **Lecture 节点**：完成 `/study` 后按上述时间表复习
- **Review Session 记录**：写入 `08_Courses/<Course>/Reviews/`，每次复习后追加条目并更新"自测结果"与"知识缺口"
