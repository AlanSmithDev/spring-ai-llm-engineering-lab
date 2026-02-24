# use-cases —— 可运行业务用例

把前面各层能力组合成端到端可运行的应用，每个都是一个独立 Spring Boot 模块，可用 `gradlew bootRun` 启动。

## 模块

### `chatbot`
最简单的对话机器人，基于 Ollama 本地模型。适合做第一个上手实验。

### `question-answering`
完整 RAG 问答服务：文档经 `data-ingestion` 入库 PGVector → 问题检索 → 模型作答并附引用来源。最贴近真实「企业知识库」场景。

### `semantic-search`
语义检索：把文本转向量后用相似度搜索，而非关键词匹配。

### `structured-data-extraction`
从非结构化文本抽取结构化字段（如订单、简历信息），输出强类型对象。

### `text-classification`
文本分类（如情感、意图识别），演示 few-shot / 标签约束的输出控制。

## 运行
每个子目录下有独立 `README.md` 与 `application.properties`。先在根目录 `make db-up` 起依赖，再进入对应模块运行。
