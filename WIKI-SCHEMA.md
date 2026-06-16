# WIKI-SCHEMA — 半导体产业知识库

## 目录结构

```
semiconductor-wiki/
├── WIKI-SCHEMA.md    # 本文件：告诉 LLM 如何维护 Wiki
├── raw/              # 原始资料（不可变，只读）
│   ├── papers/       # PDF 论文
│   ├── articles/     # Markdown/Web 文章
│   ├── images/       # 图片资源
│   └── data/         # 数据文件
├── wiki/             # LLM 维护（用户只读，LLM 全权负责）
│   ├── index.md      # 内容目录
│   ├── log.md        # 操作日志（只追加）
│   ├── overview.md   # 半导体产业研究概述
│   ├── entities/     # 实体页：公司、人物、机构
│   ├── concepts/     # 概念页：技术、工艺、标准
│   ├── papers/       # 论文/文章摘要页
│   └── synthesis/    # 综合分析（Query 产物存回）
```

## 领域分类

### entities/ — 实体页
- **公司**：台积电、中芯国际、华为海思、ASML、NVIDIA、长江存储等
- **人物**：谢志峰、张忠谋、黄仁勋等
- **机构**：SEMI、SIA、中国半导体行业协会等

### concepts/ — 概念页
- **技术/工艺**：FinFET、GAA、EUV光刻、Chiplet、先进封装、RISC-V
- **产业链环节**：设计（EDA/IP）、制造（Foundry）、封测、设备、材料
- **政策/标准**：芯片法案、出口管制、国产替代、信创

### papers/ — 论文/文章摘要页
- 学术论文（arXiv、IEEE等）
- 产业报告（SEMI、IC Insights等）
- 深度分析文章

### synthesis/ — 综合分析
- Query 产生的有价值的对比分析、趋势判断、观点梳理
- 按主题组织，如 `中国半导体突围路径.md`、`EUV_vs_DUV对比.md`

## 页面格式

### 实体页（entities/）
```markdown
---
type: entity
category: 公司 | 人物 | 机构
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
tags: []
---

# 实体名称

## 概述
简要介绍。

## 关键事实
- 事实1
- 事实2

## 相关实体
- [[另一实体]]

## 相关概念
- [[相关概念]]

## 笔记
```

### 概念页（concepts/）
```markdown
---
type: concept
category: 技术/工艺 | 产业链 | 政策/标准
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: []
tags: []
---

# 概念名称

## 定义
是什么。

## 发展历程
关键时间节点。

## 关键参与者
- [[公司A]]
- [[公司B]]

## 与中国半导体
关联分析。

## 相关概念
- [[相关概念]]

## 笔记
```

### 论文/文章摘要页（papers/）
```markdown
---
type: source-summary
authors: []
year: YYYY
source: raw/...
created: YYYY-MM-DD
tags: []
---

# 标题

## 核心观点
主要论点。

## 关键数据/事实
- 数据点1
- 数据点2

## 与 Wiki 的关系
- [[相关实体]]
- [[相关概念]]

## 引文/摘录
值得保存的原文段落。

## 笔记
```

## 工作流

### Ingest
1. 资料存到 `raw/` 对应子目录
2. 读取内容，讨论关键要点
3. 在 `wiki/papers/` 创建摘要页
4. 更新/创建相关实体页和概念页
5. 更新 `wiki/index.md`
6. 追加 `wiki/log.md`：`## [YYYY-MM-DD] ingest | 标题`
7. 汇报触及页面数

### Query
1. 读 `wiki/index.md` 定位相关页面
2. 深入阅读，综合回答，引用来源
3. 有价值分析存回 `wiki/synthesis/`
4. 追加 `wiki/log.md`：`## [YYYY-MM-DD] query | 问题摘要`

### Lint
1. 扫描：矛盾、过时声明、孤儿页、缺失概念页、断链
2. 自动修复可修复项
3. 报告需人工判断项
4. 追加 `wiki/log.md`：`## [YYYY-MM-DD] lint | 结果摘要`

## 交叉引用

使用 `[[页面名]]` 格式，如 `[[台积电]]`、[[Chiplet]]`。
VSCode 中安装 Markdown Links 插件可点击跳转。

## 命名约定

- 实体页：公司/机构全称（如 `台积电.md`、`ASML.md`），人物用中文名
- 概念页：技术术语用英文缩写/全称（如 `EUV光刻.md`、`Chiplet.md`）
- 论文页：`作者_年份_关键词.md`
- 文件路径使用相对于 `wiki/` 的路径
