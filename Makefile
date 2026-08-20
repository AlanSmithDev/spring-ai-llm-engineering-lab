# Spring AI 本地开发快捷命令
# 依赖：docker / docker compose

.PHONY: help db-up db-down db-logs db-psql ollama-pull clean

help: ## 查看可用命令
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | \
		awk 'BEGIN {FS = ":.*?## "}; {printf "  \033[36m%-12s\033[0m %s\n", $$1, $$2}'

db-up: ## 启动 PGVector + Ollama
	docker compose --env-file .env up -d
	@echo "PGVector: localhost:5432 | Ollama: localhost:11434"

db-down: ## 停止并删除容器（保留数据卷）
	docker compose --env-file .env down

db-logs: ## 查看依赖服务日志
	docker compose --env-file .env logs -f

db-psql: ## 进入 PGVector 命令行
	docker compose --env-file .env exec postgres-pgvector \
		psql -U ${POSTGRES_USER:-postgres} -d ${POSTGRES_DB:-spring_ai}

ollama-pull: ## 拉取一个本地模型（默认 qwen2.5:3b）
	docker compose --env-file .env exec ollama \
		ollama pull ${MODEL:-qwen2.5:3b}

clean: ## 停止并清空数据卷
	docker compose --env-file .env down -v
