# mcp —— 模型上下文协议（Model Context Protocol）

MCP 是让大模型安全调用外部工具/数据源的开放协议。本分组演示在 Spring AI 中接入 MCP 客户端。

## 模块

### `mcp-clients/mcp-brave`
接入 Brave Search 的 MCP Server，让模型具备「联网搜索」能力。典型用法是把 MCP 工具注册为 `ToolCallback`，模型即可在对话中自主触发搜索。

## 扩展思路
- MCP Server 支持 `stdio` 与 `SSE` 两种传输模式。
- 可把任意内部 API 封装为 MCP Server，使模型在不变更业务代码的前提下获得新能力。
