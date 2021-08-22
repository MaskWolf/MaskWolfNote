1. 拉取MySQL:5.7Docker镜像

```bash
docker pull mysql:5.7
```

2. 运行镜像
   1. 进行了 端口映射

   2. 进行了文件挂载

   3. 设置了数据库 root 账户密码

```bash
docker run -p 3306:3306 --name mysql --restart=always \
-e TZ=Asia/Shanghai \
-v /mydata/mysql/log:/var/log/mysql \
-v /mydata/mysql/data:/var/lib/mysql \
-v /mydata/mysql/conf:/etc/mysql \
-e MYSQL_ROOT_PASSWORD=root \
-d mysql:5.7
```

