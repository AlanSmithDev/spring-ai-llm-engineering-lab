# patterns —— Spring AI 通用能力模式

跨用例复用的核心技巧集合。每个模式都有 Ollama（本地）与 OpenAI（云端）双实现，便于对照学习。

## 子分组

### `prompts`（提示词）
- `prompts-basics`：直接拼字符串 vs 模板化。
- `prompts-messages`：system / user / assistant 多角色消息构造。
- `prompts-templates`：`PromptTemplate` 参数化模板与变量绑定。

### `memory`（记忆）
- `memory-basics`：基于内存的对话记忆。
- `memory-jdbc`：JDBC 持久化，重启不丢上下文。
- `memory-vector-store`：用向量库做长期记忆检索。
- `memory-spring-security`：记忆与 Spring Security 身份绑定（多租户隔离）。

### `guardrails`（护栏）
- `guardrails-input`：输入侧敏感词 / 越权拦截。
- `guardrails-output`：输出侧合规过滤。

### `structured-output`（结构化输出）
- `structured-output-ollama` / `-openai`：让模型输出强类型 Java 对象（JSON → POJO）。

### `multimodality`（多模态）
- 图文混合输入（Mistral / Ollama / OpenAI）。

### `tool-calling`（工具调用）
- 让模型在回答时调用你提供的函数（如查天气、算数），各供应商实现对照。

## 设计关注点
- **Advisor 链**：多数能力以 Advisor 形式挂载在 `ChatClient` 上，可叠加组合。
- **可替换性**：同一模式 Ollama/OpenAI 双实现，凸显供应商无关设计。
