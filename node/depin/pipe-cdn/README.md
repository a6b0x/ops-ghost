


```bash
cd /root/ops-ghost/node/depin/pipe-cdn
sudo docker build -t pipe-node .

sudo docker run -d \
  --name pipe-node \
  -p 80:80 \
  -p 443:443 \
  -p 8081:8081 \
  -p 9090:9090 \
  --restart always \
  pipe-node

docker exec pipe-node /opt/pipe/pop status
docker exec pipe-node /opt/pipe/pop earnings
```


参考
[PipeCDN-Node-Guide](https://github.com/aotlover9-base-eth/PipeCDN-Node-Guide/)
