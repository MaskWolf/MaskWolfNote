- 进入容器中的控制台

  ```bash
  docker exec -it 容器名/容器id /bin/bash
  ```

- 查看当前 Docker 管理的镜像

  ```bash
  docker images
  ```

- 查看所有的容器进程

  ```bash
  docker ps -a
  ```

- Centos7 Docker操作

  ```bash
  # 开启Docker服务
  systemctl start docker
  
  # 设置Docker开机自启动
  systemctl enable docker
  ```

- 重启 Docker 容器

  ```
  docker restart 容器名/容器id
  ```

- 更新Docker 容器配置

  ```bash
  # 设置重启时自动运行
  docker update 容器名/容器id --restart=always
  ```

- 查看日志

  ```bash
  docker logs 容器名/容器id
  ```

- 删除镜像

  ```xbash
  docker rmi 镜像名/镜像id
  ```

  