
```bash

# log: failed to sufficiently increase receive buffer size (was: 208 kiB, wanted: 7168 kiB, got: 416 kiB). 
sysctl -w net.core.rmem_max=8000000
sysctl -w net.core.wmem_max=8000000

sysctl net.core.rmem_max net.core.wmem_max

sudo swapoff -a
swapoff /swapfile
rm /swapfile

fallocate -l 16G /swapfile
chmod 600 /swapfile
mkswap /swapfile
swapon /swapfile

free -h

du -hsc ./data/* 

```