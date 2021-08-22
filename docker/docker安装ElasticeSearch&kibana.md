ElasticeSearch & kibana

[官方安装文档](https://www.elastic.co/guide/en/kibana/current/docker.html)

1. 拉取镜像

   ```bash
   docker pull elasticsearch:7.9.3
   docker pull kibana:7.9.3
   ```

2. 运行容器

   ```bash
   mkdir -p /mydata/elasticsearch/config
   mkdir -p /mydata/elasticsearch/plugins
   echo "http.host: 0.0.0.0">>/mydata/elasticsearch/config/elasticsearch.yml
   
   docker run --name elasticsearch \
   -p 9200:9200 -p 9300:9300 \
   -e TZ=Asia/Shanghai \
   -e "discovery.type=single-node" \
   -e ES_JAVA_OPTS="-Xms64m -Xmx512m" \
   -v /mydata/elasticsearch/config/elasticsearch.yml:/usr/share/elasticsearch/config/elasticsearch.yml \
   -v /mydata/elasticsearch/data:/usr/share/elasticsearch/data \
   -v /mydata/elasticsearch/plugins:/usr/share/elasticsearch/plugins \
   -d elasticsearch:7.9.3
   
   docker run --name kibana --link elasticsearch:elasticsearch \
   -p 5601:5601 \
   -e TZ=Asia/Shanghai \
   -d kibana:7.9.3
   
   # 添加ik分词器插件
   mkdir /mydata/elasticsearch/plugins/ik
   cd /mydata/elasticsearch/plugins/ik
   wget https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.9.3/elasticsearch-analysis-ik-7.9.3.zip
   unzip elasticsearch-analysis-ik-7.9.3.zip
   
   # 配置自定义词库
   vim /mydata/elasticsearch/plugins/ik/config/IKAnalyzer.cfg.xml
   
   <!--用户可以在这里配置远程扩展字典 -->
   <entry key="remote_ext_dict">http://192.168.121.200/es/fenci.txt</entry>
   ```