1. 拉取`Redis`镜像

   ```bash
   docker pull redis
   ```

2. 运行容器实例

   ```bash
   docker run --name redis --restart=always \
   -e TZ=Asia/Shanghai \
   -p 6379:6379 \
   -v /mydata/redis/conf/redis.conf:/etc/redis/redis.conf \
   -v /mydata/redis/data:/data \
   -d redis redis-server /etc/redis/redis.conf --appendonly yes
   ```

   `--appendonly yes`配置持久化策略