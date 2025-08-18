VPS 部署

```bash
# 1 中间件+网络
cd ops-ghost/infra
docker compose up -d
docker compose ps

# 查看网络
docker network ls

# 测试
# ADDRESS sc:9003
fluvio profile list

nc -v sc 9003

# PUBLIC spu:9010
fluvio cluster spu list

fluvio topic list
fluvio topic create quickstart-topic
fluvio produce quickstart-topic
fluvio consume quickstart-topic -B -d

# 2 应用
cd app/
docker compose up -d

fluvio consume uniswap-v2-factoty-event -B -d
fluvio consume univ2-factoty-test -B -d

```

Fluvio测试
```bash
fluvio hub smartmodule download infinyon/jolt@0.4.1
fluvio consume univ2-factoty-test --beginning --transforms-file dataflow/uni-transforms.yml 
cdk deploy start -c dataflow/uni-trans.yml 
```



RisingWave 测试
```bash
# connect to risingwave
psql -h localhost -p 4566 -d dev -U root
# create database
CREATE DATABASE test;
\c test
# list all tables
\dt
# exit
\q
```