[https://www.cnblogs.com/eelve/p/12679125.html](https://www.cnblogs.com/eelve/p/12679125.html)

https://blog.csdn.net/long199366/article/details/111356619

```bash
# 查看Windows保留端口
netsh interface ipv4 show excludedportrange protocol=tcp
# 排除保留端口
netsh int ipv4 add excludedportrange protocol=tcp startport=3306 numberofports=1
```

