VPS 部署

```bash
#  中间件+网络
cd ops-ghost/infra
docker compose up -d
docker compose ps

# 查看网络
docker network ls


#  消息队列设置
nats --server=nats-server:4222 stream add ETH_UNIV2_FACTORY --subjects="eth.univ2.factory.>" \
  --storage=file \
  --defaults    
nats --server=nats-server:4222 stream add ETH_UNIV2_PAIR --subjects="eth.univ2.pair.>" \
  --storage=file \
  --defaults    
nats --server=nats-server:4222 stream ls

#  数据库设置
CREATE DATABASE testdb;

CREATE TABLE price_ticks (
  time TIMESTAMPTZ NOT NULL,

  pair_address TEXT NOT NULL,
  token0_address TEXT NOT NULL,
  token0_symbol TEXT NOT NULL,
  token0_reserve NUMERIC NOT NULL, 
  token1_address TEXT NOT NULL,
  token1_symbol TEXT NOT NULL,
  token1_reserve NUMERIC NOT NULL, 

  token0_token1 DOUBLE PRECISION NOT NULL, 
  token1_token0 DOUBLE PRECISION NOT NULL,

  block_number BIGINT NOT NULL,
  transaction_hash TEXT NOT NULL
);

SELECT create_hypertable('price_ticks', by_range('time'));


#  应用
cd app/
docker compose up -d


```