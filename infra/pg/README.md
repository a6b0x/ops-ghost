```bash
docker exec -it timescaledb psql -d "postgres://postgres:password@localhost/postgres"
# 列出所有数据库
\l
# 连接到特定数据库
\c testdb
# 查询所有表
\dt

```