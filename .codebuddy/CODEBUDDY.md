# research-wiki Schema

## 目录结构

```
research-wiki/
├── .codebuddy/
│   └── CODEBUDDY.md   # Schema：告诉 LLM 如何维护 Wiki
├── raw/               # 原始资料（不可变，只进不改）
│   ├── papers/        # PDF 论文
│   ├── articles/      # Markdown/Web 文章
│   ├── images/        # 图片资源
│   └── data/          # 数据文件
├── wiki/              # LLM 维护的 Wiki（LLM 全权负责）
│   ├── index.md       # 内容目录（每个页面 + 一行摘要）
│   ├── log.md         # 操作日志（只追加）
│   ├── overview.md    # 研究主题概述
│   ├── entities/      # 研究实体页
│   ├── concepts/      # 核心概念页
│   ├── papers/        # 论文摘要页
│   └── synthesis/     # 综合分析（Query 产物存回）
└── assets/            # 图片附件
```

## 核心操作

### 1. Ingest（摄入新资料）
1. 将资料保存到 `raw/` 对应子目录
2. 在 `wiki/papers/` 创建论文摘要页
3. 在 `wiki/concepts/` 更新或创建相关概念页
4. 在 `wiki/entities/` 更新或创建相关实体页
5. 更新 `wiki/index.md` 添加新页面索引
6. 追加 `wiki/log.md` 记录本次摄入

### 2. Query（对知识库提问）
1. 先读 `wiki/index.md` 找到相关页面
2. 深入阅读相关 Wiki 页面
3. 综合回答，引用具体来源
4. 有持续价值的回答存回 `wiki/synthesis/`

### 3. Lint（健康检查）
1. 扫描所有 Wiki 页面，查找矛盾、过时声明、孤立页面
2. 自动修复能发现的问题
3. 追加 `wiki/log.md`

## 规范

- Wiki 更新由用户主导策划，AI 执行写入，不能越俎代庖直接修改
- 操作日志只追加，不修改历史记录
- raw/ 目录只进不改，不可删除或修改原始资料
