
```
cd ops-ghost/agent/openclaw/
docker compose up -d openclaw-gateway

chown -R 1000:1000 ./data


docker compose run --rm openclaw-cli -v

docker compose run --rm openclaw-cli dashboard --no-open
docker compose run --rm openclaw-cli devices list
docker compose run --rm openclaw-cli devices approve <requestId>

# 查询特定供应商模型
docker compose run --rm openclaw-cli models list --provider google-antigravity
# 查看模型回退配置
docker compose run --rm openclaw-cli models fallbacks list

# 添加模型回退配置
docker compose run --rm openclaw-cli models fallbacks add qwen-portal/coder-model

# 健康检查
docker compose run --rm openclaw-cli doctor

```
