# research-wiki 📖

个人投研知识库——基于 Karpathy LLM Wiki 模式的持久化知识管理体系。

## 核心理念

和传统 RAG 不同——LLM **持续构建和维护一个持久化的 wiki**。新资料进来后，不是简单索引，而是提取关键信息、整合到现有 wiki 中、更新实体页、修订主题摘要。知识被编译一次，然后持续保持最新。

## 目录结构

```
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

在 WorkBuddy 中加载 `karpathy-wiki` skill 后使用：
- `/ingest` — 摄入新资料
- `/query` — 对知识库提问
- `/lint` — 健康检查
