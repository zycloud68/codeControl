[linux安装教程](https://zhuanlan.zhihu.com/p/79047510)
# Linux安装软件教程

### Google-Chrome

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb 
# 更新系统
sudo apt update
sudo apt upgrade
# 正式安装
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

### Typora

```bash
# or run:
# sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BA300B7755AFCFAE
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install typora
```

### Redis

```bash
# 执行sudo apt-get update更新软件包
sudo apt-get update
# 执行语句 ，输入y 确认安装并使用空间
sudo  apt-get install redis-server
# 执行完成，查看redis服务状态
ps -ef|grep redis(或者 service redis status)
# 执行命令，查看reis位置在哪里
whereis redis
# /et/redis/redis.conf
# netstat-talnp中6379端口只允许本地访问，要远程链接redis，需要注释 #bind 127.0.0.1
-- #bind 127.0.0.1
# 重启redis，命令如下
service redis restart
# 启动redis
service redis start
```

### SSH远程访问Ubuntu

在Ubuntu中是不允许远程访问，需要参照一下步骤

```bash
# 打开终端安装openssh-server软件包:
sudo apt update
sudo apt install openssh-server
# 安装完成后，SSH服务默认自动启动，你可以通过以下命令校验服务运行状态
sudo systemctl status ssh
# Ubuntu 默认使用 ufw 防火墙配置工具，如果你启用了防火墙，请确保防火墙打开了 SSH 端口
sudo ufw allow ssh
# 连接ssh-server
ssh username@ip_address
eg: walker@192.168.1.1
# 查看ip地址
ip a
```

### Nginx

```bash
# 1. 安装Nginx
sudo apt-get install nginx
# 查看nginx安装位置 
whereis nginx
# 2. 安装完成后，nginx将自动启动
sudo systemctl status nginx
# 3. 允许防火墙访问
sudo ufw allow 'Nginx Full'
# 查看验证状态
sudo ufw status
```

### Nginx配置文件结构

```java
1. 所有的 Nginx 配置文件都在/etc/nginx/目录下
2. 主要的 Nginx 配置文件是/etc/nginx/nginx.conf
3. Nginx 服务器配置文件被储存在/etc/nginx/sites-available目录下。在/etc/nginx/sites-enabled目录下的配置文件都将被 Nginx 使用
4. 最佳推荐是使用标准的命名方式。例如，如果你的域名是mydomain.com，那么配置文件应该被命名为/etc/nginx/sites-available/mydomain.com.conf
```

### Jdk1.8安装

```bash
# 下载地址
https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html
# 创建文件夹，并且移动
mkdir -p /usr/local/java/
sudo mv jdk-8u291-linux-x64.tar.gz /usr/local/java/
# 解压文件
sudo tar -zxvf ./jdk-8u291-linux-x64.tar.gz
# 修改配置文件
sudo vim /etc/profile
# 增加配置环境
export JAVA_HOME=/usr/local/java/jdk1.8.0_291
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
# 重启配置，使其生效
source /etc/profile
# 查看是否安装成功
java -version
```


