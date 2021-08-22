1. 安装`openssh-server`软件包

   ```bash
   sudo apt-get update
   sudo apt-get install openssh-server
   ```

2. 启动`ssh`服务

   ```bash
   # 生成密钥
   sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
   sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
   
   # 查看ssh服务状态
   sudo service ssh status
   # 启动ssh服务
   sudo service ssh start
   # 设置ssh服务开机自启动
   sudo service ssh enable
   ```

3. 开启防火墙的`22`端口（一般默认开启）

4. 允许使用密码登陆`SSH`

   ```bash
   # 修改ssh配置
   sudo vi /etc/ssh/sshd_config
   
   PermitRootLogin yes
   passwordAuthentication yes
   
   # 重启ssh服务器
   sudo service ssh restart
   ```