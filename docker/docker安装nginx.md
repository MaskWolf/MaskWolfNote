```bash
docker pull nginx:latest

docker run -d --name nginx -p 80:80 nginx:latest

mkdir -p /mydata/nginx/html
mkdir -p /mydata/nginx/conf
mkdir -p /mydata/nginx/logs

docker cp nginx:/etc/nginx/nginx.conf /mydata/nginx/
docker cp nginx:/etc/nginx/conf.d/default.conf /mydata/nginx/conf

docker rm -f nginx

docker run -d -p 80:80 --name nginx \
-v /mydata/nginx/html:/usr/share/nginx/html \
-v /mydata/nginx/nginx.conf:/etc/nginx/nginx.conf \
-v /mydata/nginx/logs:/var/log/nginx \
-v /mydata/nginx/conf:/etc/nginx/conf.d \
nginx:latest

```

```yml
version: "3"
services:
  nginx:
    restart: always
    image: nginx
    container_name: nginx
    hostname: nginx
    ports:
      - 80:80
    environment:
      - TZ=Asia/Shanghai
    volumes:
      - /mydata/nginx/html:/usr/share/nginx/html
      - /mydata/nginx/nginx.conf:/etc/nginx/nginx.conf
      - /mydata/nginx/logs:/var/log/nginx
      - /mydata/nginx/conf:/etc/nginx/conf.d
      
networks:
  default:
    external:
      name: network
```

