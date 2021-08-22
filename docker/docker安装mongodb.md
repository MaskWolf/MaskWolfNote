1. 拉取镜像

   ```bash
   docker pull mongo
   ```

2. 运行容器

   ```bash
   docker run  \
   --name mongodb \
   -e TZ=Asia/Shanghai \
   -p 27017:27017  \
   -v /mydata/mongodb/configdb:/data/configdb/ \
   -v /mydata/mongodb/db/:/data/db/ \
   -d mongo --auth
   ```

3. 创建管理员`admin`用户和密码

   ```bash
   # 以admin用户身份进入mongodb
   docker exec -it mongodb mongo admin
   
   # 创建一个admin管理员账号
   db.createUser({ user: 'admin', pwd: 'admin', roles: [ { role: "userAdminAnyDatabase", db: "admin" } ] });
   ```

4. 创建普通用户的密码和数据库

   ```bash
   # 以admin用户身份进入mongodb
   docker exec -it mongodb mongo admin
   
   # 对admin用户进行身份认证
   db.auth("admin", "admin");
   
   # 创建用户mall
   use mall;
   db.createUser({ user: 'mall', pwd: 'mall', roles: [ { role: "readWrite", db: "mall" } ] });
   ```