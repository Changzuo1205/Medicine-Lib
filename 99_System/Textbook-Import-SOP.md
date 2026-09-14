---
type: system
status: active
tags:
  - system/sop
created: 2026-08-11
---

# 教材导入流程 SOP（Textbook Import — Reference Registration）

> 目的：将新教材纳入知识库原始资料层 `02_Raw/Textbooks/`，登记为 **Reference / Evidence Source（长期参考资料源）**。
> 本流程只做**登记与验证**，不做知识提取（不 ingest）。

---

## 一、定位与核心原则

| 原则 | 说明 |
|------|------|
| 教材 ≠ 课程 | 教材是参考资料源，不是课程笔记生成源 |
| 教材 ≠ 老师讲授 | 教材内容不能因为"教材写了"就自动视为"老师讲过" |
| 未知不猜测 | 元信息（出版年份/ISBN 等）无法从文件确认时，如实留空，待人工补充 |
| 源文件不动 | 复制进 Vault，**不移动**、不修改原始文件 |
| Reference 身份 | 状态标记为 `reference-only / not-ingested` |

### 未来使用流程（开学后，本 SOP 不执行）

```
病理学/其他课程 PPT + 教材对应章节
→ Lecture（记录老师实际讲授）
→ 搜索已有 Concept → 复用 / 扩展 / 新建
→ Pathophysiology（仅真正病理生理机制）
→ Quiz → Wrong Answer → Review
```

---

## 二、流程总览（7 步）

```
① 定位教材文件（搜索常见位置）
② 创建目标目录 02_Raw/Textbooks/<分类>/
③ 复制教材进 Vault（保留原文件名）
④ 验证完整性（页数 / 可读性 / 低文本页 / 缺页 / 乱码）
⑤ 提取可确认的元信息（未知项留空）
⑥ 创建 README.md（元信息 + Reference 声明 + 完整性记录 + 待办）
⑦ 登记 Source-Registry（可选但建议）
```

---

## 三、命令模板（复制即用，替换 `<...>` 占位符）

### ① 定位教材文件

```powershell
# 在常见位置搜索教材（把 <关键词> 换成书名关键词，如：病理|Pathology）
$paths = @("$env:USERPROFILE\Desktop", "$env:USERPROFILE\Downloads", "$env:USERPROFILE\Documents")
Get-ChildItem -Path $paths -Recurse -Filter '*.pdf' -ErrorAction SilentlyContinue |
  Where-Object { $_.Name -match '<关键词>' } |
  Select-Object FullName, @{N='SizeMB';E={[math]::Round($_.Length/1MB,1)}}, LastWriteTime
```

### ② 创建目录 + ③ 复制教材

```powershell
# <分类> 用英文 slug，如 Pathology / Physiology / Biochemistry
New-Item -ItemType Directory -Path '02_Raw/Textbooks/<分类>' -Force | Out-Null

# 复制（-LiteralPath 支持中文路径；源文件保留）
Copy-Item -LiteralPath '<源文件完整路径，如 C:\Users\xxx\Desktop\《书名》.pdf>' `
          -Destination '02_Raw/Textbooks/<分类>/<原文件名>' -Force
```

### ④ 完整性验证（Python，用 pypdf）

> ⚠️ 避坑：中文路径/中文常量经 PowerShell stdin 传给 Python 会损坏。**用 os.listdir 枚举目录**，不要在脚本里硬编码中文文件名。

```python
import os
from pypdf import PdfReader   # 大 PDF 用 pypdf（快）；小文件也可用 pdfplumber

path = r'02_Raw/Textbooks/<分类>'          # 相对 Vault 根目录
files = [f for f in os.listdir(path) if f.lower().endswith('.pdf')]
print('In vault:', files)

pdf = os.path.join(path, files[0])
r = PdfReader(pdf)
n = len(r.pages)
print('Pages:', n)

# 遍历统计低文本页（封面/扉页/封底空文本属正常）
low = [(i+1, len((r.pages[i].extract_text() or '').strip())) for i in range(n)
       if len((r.pages[i].extract_text() or '').strip()) < 30]
print('Low-text pages (<30 chars):', len(low), f'({round(len(low)/n*100,1)}%)')
print('Low-text pages list:', low[:30])

# 连续空白段（>=3 页）→ 提示潜在缺页
runs, start, prev = [], None, None
for pg, _ in low:
    if prev is None or pg == prev + 1:
        if start is None: start = pg
    else:
        if start is not None and pg - start >= 3: runs.append((start, prev))
        start = pg
    prev = pg
if start is not None and prev - start >= 3: runs.append((start, prev))
print('Consecutive blank runs (>=3 pages):', runs)
```

### ⑤ 元信息提取（抽样确认书名页/版权页）

```python
# 书名页通常在第 2-3 页；版权页含版次/ISBN/出版年份
from pypdf import PdfReader
r = PdfReader(r'02_Raw/Textbooks/<分类>/<文件名>.pdf')
for i in [0, 1, 2, len(r.pages)-1]:
    t = (r.pages[i].extract_text() or '').strip()
    print(f'p{i+1}: {t[:200]!r}')
```

### ⑥ 创建 README.md（模板）

复制下方模板，替换 `<...>` 字段：

```markdown
---
type: reference_source
status: active
tags:
  - system/reference
  - textbook/<分类标签，如 pathology>
registered_date: <YYYY-MM-DD>
---

# <教材名称> — Reference Source 注册

## 教材元信息

| 项目 | 内容 |
|------|------|
| 教材名称 | <名称> |
| 主编 | <从书名页确认；未知留空> |
| 版次 | <第 X 版；未知留空> |
| 出版年份 | <从版权页确认；未知留空待人工补充> |
| 文件名 | <文件名>.pdf |
| 文件大小 | <大小> |
| 页数 | <页数> |
| 文件完整性 | 完整可读（详见下方检查记录） |
| 用途 | <如：下学期 XXX 课程参考教材> |
| 当前状态 | **reference-only / not-ingested** |

## Reference Source 声明

本教材仅作为**长期参考资料源（Reference / Evidence Source）**，不是课程笔记或 Concept 生成源。

- 教材内容 ≠ 老师讲授内容
- 教材内容不能因为"教材写了"就自动视为"老师讲过"
- 未来 ingest 时以课程 PPT 为准记录老师实际讲授内容，教材作为标准、完整的参考背景

## 完整性检查记录（<YYYY-MM-DD>）

| 检查项 | 结果 |
|--------|------|
| 文件存在 | ✅ |
| 页数 | <页数> |
| 可读性 | ✅ / ❌（描述） |
| 低文本页 | <N> 页（<百分比>%）：<页码列表> —— 说明是否正常（封面/扉页/封底） |
| 缺页 | 未发现 / 发现（描述） |
| OCR/文本提取 | ✅ 正常 / ⚠️（描述问题位置） |
| 已知问题 | 无 / 描述 |

## 待办

- [ ] 出版年份与 ISBN 待人工补充
- [ ] 开学后确认课程所用教材版本与此是否一致
```

### ⑦ 登记 Source-Registry（可选但建议）

编辑 `99_System/Source-Registry.md`，在 Textbooks 表中追加一行：

```markdown
| 编号 | 书名 | 作者/编者 | 版本/年份 | 状态 |
| S-TXT-00X | <教材名称> | <主编> | 第 X 版 / <年份或留空> | needs_review |
```

---

## 四、禁止事项（本流程内）

- ❌ 不执行 `/ingest`
- ❌ 不创建任何 Concept / Lecture / Exam Topic / Course / Quiz / Flashcard / Wrong Answer
- ❌ 不修改 `03_Concepts/` 任何内容（含 Pathophysiology 节点）
- ❌ 不根据教材内容批量提炼知识
- ❌ 不用模型常识补充教材缺失内容（未知元信息留空）
- ❌ 不修改 AGENTS.md
- ❌ 不修改现有模板

---

## 五、验收清单（注册报告必须包含）

1. 教材文件路径（Vault 内）
2. 教材名称 / 版本（能确认的才填写）
3. 页数
4. 文件完整性（存在 / 可读 / 缺页 / 乱码）
5. 文本提取质量
6. 发现的缺页 / 乱码 / 图表提取问题（只记录，不修复）
7. 创建或修改了哪些文件
8. 明确确认 0 项：

```
Concept 新建 = 0    Concept 修改 = 0    Lecture 新建 = 0
Course 新建  = 0    Quiz 新建 = 0        AGENTS.md 修改 = 0
```

9. 最终结论：

```
<教材名> Textbook Registration: PASS / FAIL
```

---

## 六、历史避坑记录

| # | 坑 | 对策 |
|---|----|------|
| 1 | 中文路径经 PowerShell stdin 传给 Python 时损坏（`?????.pdf`） | Python 脚本内用 `os.listdir` 枚举目录，避免硬编码中文常量 |
| 2 | 大 PDF（>30 MB）用 pdfplumber 全页遍历超时 | 用 pypdf 获取页数与文本；需精细布局时才用 pdfplumber 采样 |
| 3 | 封面 / 扉页 / 封底为空文本 | 属正常；低文本页需区分"正常空页"与"异常页" |
| 4 | 环境策略拦截 Remove-Item（temp 清理） | 删除被拦截时保留并透明说明，不强行操作 |

---

## 七、参考实例

- 2026-08-10：《病理学（第10版）》注册 → `02_Raw/Textbooks/Pathology/README.md`（完整流程示范）
- 2026-09-14：一次补齐 4 份教材登记（S-TXT-001 ~ 004）→
  - `02_Raw/Textbooks/Medical Microbiology/README.md`（文本层 ✅）
  - `02_Raw/Textbooks/Clinical Epidemiology/README.md`（**纯图像扫描版，无文本层**）
  - `02_Raw/Textbooks/Medical Immunology/README.md`（**纯图像扫描版，无文本层**）
  - `02_Raw/Textbooks/Pathology/README.md`（补齐版权页元信息：ISBN / 版次 / 出版年份）

> **经验（2026-09-14）**：步骤 ④ 必须显式判定「是否存在文本层」。仅看"页数正常、PDF 可打开"会漏判图像扫描版；
> 判定方法：抽样页 `page.extract_text()` 长度 ≈ 0（或仅为水印文字）⇒ 图像版，**不可用于逐句核对，需先 OCR**。