---
type: system
status: active
tags:
  - system/meta
---

# Medicine-Lib 系统说明

本目录存放知识库的**系统文件**，不存放医学知识。

## 目录结构

```
Medicine-Lib/
├── 00_Dashboard/   # 首页与学习总览
├── 01_Inbox/       # 临时输入
├── 02_Raw/         # 原始资料（尽量保持原样）
├── 03_Concepts/    # 核心知识节点
├── 04_Clinical/    # 临床推理
├── 05_Study/       # 主动学习
├── 06_Specialties/ # 专科导航
├── 07_MOCs/        # 知识导航页
├── 08_Courses/     # 课程上下文层（Course / Lecture / Exam Topic / Review Session）
├── 99_System/      # 系统规则与日志
└── AGENTS.md       # 知识库规范
```

## 核心原则

1. **知识优先于笔记** — 重要知识尽量成为独立、可链接、可复用的知识节点
2. **原始资料与整理知识分离** — 02_Raw 保持原样，知识写入 03_Concepts
3. **链接优先** — 用 [[链接]] 而非重复复制
4. **来源优先** — 医学事实必须有明确来源
5. **不确定性显式表达** — 用 evidence_level 与 source_status 标记

## 本目录文件

- [[Knowledge-Status]] — 知识状态跟踪（Knowledge Gaps / Needs Review / 冲突 / 无来源 / 过时）
- [[Source-Registry]] — 来源登记表（教材 / 指南 / 文献 / 讲座）
- [[Change-Log]] — 结构变更日志
- [[Ingest-SOP]] — `/ingest` 详细作业流程（预检 / 概念提取 / 写作安全规则 / **课程上下文层同步 §3.5** / 后验 / 并行 agent 协作）
- [[Textbook-Import-SOP]] — 教材导入流程（Reference Registration 标准操作流程 + 命令模板）
- [[99_System/Templates/01_Disease|Templates]] — 知识节点模板（20 个）
- [[99_System/Archive/|Archive]] — 退役概念与退役题目存档（不属于活跃知识层）
