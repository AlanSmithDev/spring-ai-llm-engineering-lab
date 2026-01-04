# rag —— 检索增强生成（RAG）

RAG 把「外部知识检索」与「大模型生成」结合，让回答有据可依。本分组给出四种编排范式，复杂度递增。

## 模块

### `rag-sequential/rag-naive`（朴素 RAG）
最基础链路：文档向量化入库 → 问题向量检索 → 取 Top-K 片段 → 拼进 Prompt 让模型作答。适合入门。

### `rag-sequential/rag-advanced`（进阶顺序 RAG）
在朴素基础上加入：查询重写（query rewrite）、多查询扩展（multi-query）、重排序（rerank）等提升召回与精度的手段。

### `rag-conditional`（条件 RAG）
先判断问题是否需要检索；仅当命中「知识库可回答」条件时才走向量库，否则直接对话。降低无谓检索开销。

### `rag-branching`（分支 RAG）
根据问题类型路由到不同检索策略（如：事实类走向量检索、计算类走工具调用），是多 Agent 路由的雏形。

## 关键组件
- `VectorStore`：默认 PGVector。
- `QuestionAnswerAdvisor`：Spring AI 提供的 RAG Advisor，封装检索→拼装。
- `Document` / `Transformer`：来自 `data-ingestion` 的文档流水线。

运行 `use-cases/question-answering` 可看到一个完整可用的 RAG 服务。
