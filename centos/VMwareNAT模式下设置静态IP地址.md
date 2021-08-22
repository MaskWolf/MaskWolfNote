## Centos7

```bash
# 网卡配置所在目录
cd /etc/sysconfig/network-scripts

# 备份网卡原有配置
cp ifcfg-xxxxx ifcfg-xxxxx.bak

# 修改网卡配置
vi ifcfg-xxxxx

# ifconfig命令
yum install net-tools
```

网卡配置修改 `ifcfg-xxxxx` 为以下内容

```bash
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=976c160d-5a1b-4e8f-9f1c-c8d7a1af13cf
DEVICE=ens33
ONBOOT=yes
DNS1=114.114.114.114
IPADDR=192.168.200.128
NETMASK=255.255.255.0
GATEWAY=192.168.200.2
```
