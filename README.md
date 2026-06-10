# research-wiki 📖

个人投研知识库——基于 Karpathy LLM Wiki 模式的持久化知识管理体系。

## 核心理念

和传统 RAG 不同——LLM **持续构建和维护一个持久化的 wiki**。新资料进来后，不是简单索引，而是提取关键信息、整合到现有 wiki 中、更新实体页、修订主题摘要。知识被编译一次，然后持续保持最新。

## 目录结构

```
├── .codebuddy/
│   └── CODEBUDDY.md  # Schema 规范（CodeBuddy 自动加载）
├── raw/      # 原始资料（只进不改）
├── wiki/     # LLM 维护的知识库
│   ├── index.md     # 内容目录
│   ├── log.md       # 操作日志
│   ├── overview.md  # 研究主题概述
│   ├── entities/    # 研究实体
│   ├── concepts/    # 核心概念
│   ├── papers/      # 论文摘要
│   └── synthesis/   # 综合分析
└── assets/   # 图片附件
```

## 使用方式

在 CodeBuddy 中打开此项目，AI 会自动加载 `CODEBUDDY.md` 中的 Schema 规范。

三个核心操作（直接对 AI 说即可）：
- **Ingest**（"摄入/添加资料"） — 将新资料整合到 wiki
- **Query**（"查询/搜索"） — 对知识库提问，生成综合分析
- **Lint**（"健康检查"） — 检查 wiki 一致性
