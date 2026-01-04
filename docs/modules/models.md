# models —— 模型接入层

统一封装各类生成式 AI 模型的调用，屏蔽供应商差异。所有模块都通过 Spring AI 的 `ChatClient` / `EmbeddingClient` / `ImageClient` / `AudioClient` 抽象访问模型。

## 分组

### chat（对话模型）
| 模块 | 供应商 | 要点 |
| --- | --- | --- |
| `chat-openai` | OpenAI | 云端对话，支持流式 |
| `chat-ollama` | Ollama | 本地推理，零 API Key |
| `chat-mistral-ai` | Mistral AI | 云端对话 |
| `chat-multiple-providers` | 多供应商 | 运行时按配置切换模型 |

### embedding（向量化）
| 模块 | 供应商 |
| --- | --- |
| `embedding-openai` | OpenAI embeddings |
| `embedding-ollama` | Ollama embeddings（本地） |
| `embedding-mistral-ai` | Mistral embeddings |
| `embedding-transformers` | 本地 Transformers（无外部依赖） |

### image（图像）
- `image-openai`：文生图 / 图生图。

### audio（音频）
- `speech-to-text-openai`：语音转文本。
- `text-to-speech-openai`：文本转语音。

## 设计关注点
- **抽象优先**：业务代码只依赖 `ChatClient` 接口，换供应商改配置即可。
- **本地兜底**：Ollama / Transformers 系列可完全离线运行，适合无 Key 学习。

详见各子模块目录下的 `README.md`。
