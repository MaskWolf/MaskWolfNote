~~~bash
# 查看docker mysql的ip地址
docker container inspect mysql|grep -wA 30 "Networks"

# 启动一个简单的nacos，用于复制配置文件
docker run --env MODE=standalone --name nacos -d -p 8848:8848 nacos/nacos-server
sudo docker cp nacos:/home/nacos/conf /mydata/nacos/conf
docker rm -f nacos

# 启动nacos
docker run -d \
-e TZ="Asia/Shanghai" \
-e MODE=standalone \
-p 8848:8848 \
-p 9848:9848 \
--name nacos --restart=always \
-v /mydata/nacos/logs/:/home/nacos/logs \
-v /mydata/nacos/conf/:/home/nacos/conf \
nacos/nacos-server

# 配置mysql数据库信息
sudo vim /mydata/nacos/application.properties
docker restart nacos
~~~

~~~properties
# spring
server.servlet.contextPath=${SERVER_SERVLET_CONTEXTPATH:/nacos}
server.contextPath=/nacos
server.port=${NACOS_APPLICATION_PORT:8848}
spring.datasource.platform=${SPRING_DATASOURCE_PLATFORM:mysql}
nacos.cmdb.dumpTaskInterval=3600
nacos.cmdb.eventTaskInterval=10
nacos.cmdb.labelTaskInterval=300
nacos.cmdb.loadDataAtStart=false
db.num=${MYSQL_DATABASE_NUM:1}
db.url.0=jdbc:mysql://${MYSQL_SERVICE_HOST:172.17.0.2}:${MYSQL_SERVICE_PORT:3306}/${MYSQL_SERVICE_DB_NAME:interviewqa-config}?${MYSQL_SERVICE_DB_PARAM:characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true}
db.url.1=jdbc:mysql://${MYSQL_SERVICE_HOST}:${MYSQL_SERVICE_PORT:3306}/${MYSQL_SERVICE_DB_NAME}?${MYSQL_SERVICE_DB_PARAM:characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true}
db.user=${MYSQL_SERVICE_USER:root}
db.password=${MYSQL_SERVICE_PASSWORD:root}
### The auth system to use, currently only 'nacos' is supported:
nacos.core.auth.system.type=${NACOS_AUTH_SYSTEM_TYPE:nacos}
~~~

