```shell
# 拉取docker容器图形化管理工具portainer
docker pull portainer/portainer

# 运行镜像
docker run -p 8000:8000 -p 9000:9000 --name portainer \
--restart=always \
-e TZ="Asia/Shanghai" \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /mydata/portainer/data:/data \
-d portainer/portainer

# 用户/密码
admin/ljcadmin
```

访问地址：[http://127.0.0.1:9000](http://127.0.0.1:9000)