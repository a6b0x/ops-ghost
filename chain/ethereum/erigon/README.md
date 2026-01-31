
```bash

# log: failed to sufficiently increase receive buffer size (was: 208 kiB, wanted: 7168 kiB, got: 416 kiB). 
sysctl -w net.core.rmem_max=8000000
sysctl -w net.core.wmem_max=8000000

sysctl net.core.rmem_max net.core.wmem_max

# 关闭所有已知的 Swap。
sudo swapoff -a
# 确保名为 /swapfile 的特定文件被关闭
swapoff /swapfile
# 删除已不再被使用的 /swapfile 文件
rm /swapfile

# 创建 swap 文件
fallocate -l 32G /swapfile
# 设置正确的文件权限
chmod 600 /swapfile
# 将文件设置为 Swap 区域
mkswap /swapfile
# 启用 Swap
swapon /swapfile
# 验证
free -h

du -hsc ./data/* 

```

