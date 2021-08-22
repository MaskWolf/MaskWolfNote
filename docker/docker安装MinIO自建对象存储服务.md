1. 拉取镜像

   ```bash
   docker pull minio/minio
   ```

2. 运行容器实例

   ```bash
   docker run -p 9090:9000 --name minio \
   -v /mydata/minio/data:/data \
   -v /mydata/minio/config:/root/.minio \
   -e TZ=Asia/Shanghai \
   -d minio/minio server /data
   ```

3. 访问web管理界面

   [http://localhost:9090](http://localhost:9090)

    默认`Access Key`和`Secret`都是`minioadmin` 

4. 官方文档

   [https://docs.min.io/cn/](https://docs.min.io/cn/)

