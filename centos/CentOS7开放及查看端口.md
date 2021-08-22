```bash
# 查看防火墙所有开放的端口
firewall-cmd --zone=public --list-ports

# 开放5672端口
firewall-cmd --zone=public --add-port=5672/tcp --permanent

# 关闭5672端口
firewall-cmd --zone=public --remove-port=5672/tcp --permanent

# 配置立即生效
firewall-cmd --reload
```

