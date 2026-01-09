# 架构总览

本工程是「以 Spring AI 为核心的生产级生成式 AI 应用样例集合」，按**能力分层**组织成 7 个顶级分组。阅读建议从 `models` 入手，再依次看 `patterns`、`rag`、`use-cases`，最后看 `mcp` / `observability` / `data-ingestion` 这类横向支撑能力。

## 分层与依赖

```
                     ┌─────────────────────────────┐
   业务用例层         │  use-cases                 │  chatbot / QA / semantic-search /
                     │  (chatbot, qa, search ...)  │  structured-extraction / classification
                     └───────────────┬─────────────┘
                                     │ 组合
                     ┌───────────────┴─────────────┐
   能力层             │  rag / patterns / mcp       │  RAG 流 / Prompt / Memory / Guardrails /
                     │                            │  Tool Calling / Multimodality / MCP
                     └───────────────┬─────────────┘
                                     │ 调用
                     ┌───────────────┴─────────────┐
   模型接入层         │  models                    │  Chat / Embedding / Image / Audio
                     │  (openai / ollama / mistral)│  统一 ChatClient / EmbeddingClient 抽象
                     └───────────────┬─────────────┘
                                     │ 依赖
   ┌──────────────────────┐   ┌──────┴───────────────┐
   │  observability        │   │  data-ingestion       │
   │  (metrics / tracing)  │   │  (readers / splitters) │
   └──────────────────────┘   └──────────────────────┘
```

## 关键抽象

- **ChatClient / EmbeddingClient**：Spring AI 对模型供应商的统一门面，使 OpenAI / Ollama / Mistral 可互换。
- **Advisor**：Spring AI 的拦截器链（如 `QuestionAnswerAdvisor`、`VectorStoreChatMemoryAdvisor`），用于在请求前后注入 RAG 上下文、记忆、护栏。
- **VectorStore**：向量库抽象，PGVector 为本工程默认实现。
- **Document / Transformer**：数据摄入的读取→切分→元信息增强流水线。

## 推荐阅读顺序

1. `models/chat/chat-ollama` —— 最小可运行的对话样例。
2. `patterns/prompts` —— Prompt 模板与消息构造。
3. `patterns/memory` —— 多轮对话记忆（基础 / JDBC / 向量库 / Spring Security）。
4. `rag/rag-sequential/rag-naive` —— 朴素 RAG 全链路。
5. `use-cases/question-answering` —— 完整问答用例（RAG + PGVector）。

分模块细节见 `docs/modules/*.md`。
