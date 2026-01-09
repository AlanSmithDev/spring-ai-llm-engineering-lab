# observability —— 可观测性

生成式 AI 应用最大的运维难点是「黑盒」：请求慢在哪？回答为何偏离？本分组演示对模型调用与向量库访问的埋点。

## 模块

### `models`（模型调用埋点）
- `observability-models-ollama` / `-openai` / `-mistral-ai`
  - 通过 Micrometer 暴露调用时延、Token 用量、成功率等指标。
  - 结合 Spring Boot Actuator 输出 `/actuator` 端点。

### `vector-stores`（向量库埋点）
- `observability-vector-stores-pgvector`
  - 监控向量检索耗时、命中数、查询模式。

## 价值
- 生产环境排障：定位是模型慢、向量库慢还是网络慢。
- 成本监控：Token 维度计费与告警基础。
