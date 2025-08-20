```bash
nc -zv nats-server 4222
# 创建流
nats --server=nats-server:4222 stream add test-stream --subjects="test.*"
# 查看所有流
nats --server=nats-server:4222 stream ls
# 查看流详细信息
nats --server=nats-server:4222 stream info test-stream
# 发布信息
nats --server=nats-server:4222 pub test "hello"
# 消费者管理
nats --server=nats-server:4222 consumer add test-stream test-consumer
nats --server=nats-server:4222 consumer rm test-stream test-consumer

```