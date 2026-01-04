# data-ingestion —— 数据摄入流水线

RAG 的前提是把文档变成可检索的向量。本分组实现「读取 → 切分 → 元信息增强」的文档处理链路，均基于 Ollama 本地模型。

## 子分组

### `document-readers`（文档读取）
| 模块 | 支持格式 |
| --- | --- |
| `document-readers-pdf-ollama` | PDF |
| `document-readers-markdown-ollama` | Markdown |
| `document-readers-json-ollama` | JSON |
| `document-readers-text-ollama` | 纯文本 |
| `document-readers-tika-ollama` | 通用格式（Apache Tika） |

### `document-transformers`（文档转换）
| 模块 | 作用 |
| --- | --- |
| `document-transformers-splitters-ollama` | 按长度/语义切分，控制单块 token 数 |
| `document-transformers-metadata-ollama` | 自动生成并写入元信息（标题、摘要、关键词），提升检索精度 |

## 设计关注点
- **Reader/Transformer 可插拔**：新格式只需实现对应接口。
- **切分策略决定 RAG 上限**：块太大召回噪声高，太小丢失上下文，需按业务调参。
- **元信息增强**：在检索阶段可作为过滤条件，是进阶 RAG 的常用手段。
