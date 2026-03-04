# Spring AI LLM 工程实验室（spring-ai-llm-engineering-lab）

基于 Java 21+ / Spring Boot 3 / Spring AI 的**生成式 AI 应用工程样例库**。覆盖大模型接入、Embedding 向量化、RAG 检索增强、Prompt 工程、Tool Calling（工具调用）、Memory 记忆、Guardrails 护栏、多模态、MCP 模型上下文协议、可观测性，以及可直接运行的业务用例（聊天机器人、问答、语义检索、结构化抽取、文本分类）。

> ⚠️ **原始项目与版权**：本仓库是 [`ThomasVitale/llm-apps-java-spring-ai`](https://github.com/ThomasVitale/llm-apps-java-spring-ai)（Apache-2.0）的学习/二次整理版本。原始源码版权归原作者所有，本仓库保留其 `LICENSE` 与 `NOTICE`，并在其上补充了**本地开发基础设施（docker-compose / Makefile / .env.example）** 与**中文模块文档**。修改声明见 `NOTICE`。

## 技术栈

- Java 21+、Spring Boot 3、Spring AI
- 多模型供应商抽象：OpenAI / Ollama（本地）/ Mistral AI
- 向量库：PostgreSQL + PGVector
- 构建：Gradle（含 `gradlew` 包装器，无需预先安装 Gradle）

## 模块地图

| 分组 | 说明 | 文档 |
| --- | --- | --- |
| `models` | 模型接入：Chat / Embedding / Image / Audio，多 provider 统一抽象 | [docs/modules/models.md](docs/modules/models.md) |
| `rag` | 检索增强：Naive / Sequential / Conditional / Branching 四种 RAG 流 | [docs/modules/rag.md](docs/modules/rag.md) |
| `patterns` | Spring AI 通用模式：Prompts / Memory / Guardrails / Structured Output / Multimodality / Tool Calling | [docs/modules/patterns.md](docs/modules/patterns.md) |
| `use-cases` | 可运行业务用例：Chatbot / QA / Semantic Search / 结构化抽取 / 文本分类 | [docs/modules/use-cases.md](docs/modules/use-cases.md) |
| `mcp` | MCP 模型上下文协议客户端（如 Brave 搜索） | [docs/modules/mcp.md](docs/modules/mcp.md) |
| `observability` | 模型与向量库的可观测性埋点 | [docs/modules/observability.md](docs/modules/observability.md) |
| `data-ingestion` | 文档读取（PDF/Markdown/JSON/Text/Tika）与切分、元信息标注 | [docs/modules/data-ingestion.md](docs/modules/data-ingestion.md) |

> 架构总览与阅读顺序见 [docs/architecture.md](docs/architecture.md)。

## 本地环境（一键起依赖）

本仓库补充了 `docker-compose.yml` 与 `Makefile`，用于本地拉起 PGVector（向量库）与 Ollama（本地推理）：

```bash
cp .env.example .env      # 按需填写 OPENAI_API_KEY 等
make db-up                # 启动 PostgreSQL+PGVector 与 Ollama
make db-down             # 停止并清理
```

## 快速开始

```bash
# 选择一个具体模块运行，例如聊天机器人
cd use-cases/chatbot
../../gradlew bootRun
```

每个子模块目录下都自带 `README.md` 与运行说明；环境变量（API Key、模型名、向量库连接）通过 `application.properties` 读取，详见 `.env.example`。

## 目录说明

- `buildSrc/`：共享 Gradle 构建约定（依赖版本、插件配置）
- `gradle/` + `gradlew`：Gradle 包装器，保证构建一致性
- `docs/`：本仓库补充的中文架构与模块文档

## License

原始代码 Apache License 2.0，见 `LICENSE`。本仓库补充内容（文档、docker-compose、Makefile 等）在保留署名的前提下遵循同一许可证。
