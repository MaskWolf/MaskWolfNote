1. 拉取含web管理界面的rabbitMQ镜像

    ```bash
    docker pull rabbitmq:management
    ```

2. 运行容器

    ```bash
    docker run --name rabbitmq \
    -e TZ=Asia/Shanghai \
    --hostname rabbitmq \
    -p 5672:5672 -p 15672:15672 \
    -v /mydata/rabbitmq/data:/var/lib/rabbitmq \
    -v /mydata/rabbitmq/log:/var/log/rabbitmq \
    -v /mydata/rabbitmq/conf:/etc/rabbitmq \
    -e RABBITMQ_DEFAULT_VHOST=rabbitmq_vhost  \
    -e RABBITMQ_DEFAULT_USER=admin \
    -e RABBITMQ_DEFAULT_PASS=admin \
    -d rabbitmq:management
    ```

    - --hostname  主机名（RabbitMQ的一个重要注意事项是它根据所谓的 “节点名称” 存储数据，默认为主机名）

    - -e 指定环境变量（RABBITMQ_DEFAULT_VHOST：默认虚拟机名；RABBITMQ_DEFAULT_USER：默认的用户名；RABBITMQ_DEFAULT_PASS：默认用户名的密码）

3. web管理界面
	[http://localhost:15672](http://localhost:15672)

