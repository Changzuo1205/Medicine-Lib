---
type: navigation
status: active
tags:
  - system/navigation
---

# 03_Concepts — 核心知识库

存放正式知识节点。每个重要医学概念尽可能建立独立 Markdown 文件。

## 子目录

- [[Diseases]] — 疾病
- [[Symptoms]] — 症状
- [[Signs]] — 体征
- [[Tests]] — 检查
- [[Drugs]] — 药物
- [[Procedures]] — 操作/治疗技术
- [[Physiology]] — 正常生理学机制
- [[Pathophysiology]] — 病理生理机制

## 使用规则

1. 每个概念一个文件，遵循 [[99_System/Templates/01_Disease|模板]]
2. 使用 YAML Frontmatter（type / status / evidence_level / source_status / last_reviewed）
3. 优先建立双向链接，而非复制内容
4. 不确定的证据标记 needs_review / unsourced
5. 新建节点前先检查是否已存在同名或近似节点
6. 正常生理机制 → [[Physiology]]（模板 20_Physiology）；病理生理机制 → [[Pathophysiology]]（模板 07_Pathophysiology）
