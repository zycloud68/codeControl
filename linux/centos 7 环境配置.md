# Centos 7 安装 Java 8 以及Tomcat8

### 更新软件

```java
yum update
```

### 查看软件是否安装了java版本

```java
java -version
```

### 卸载以前安装的Jdk

```java
#查看内置的JDK
rpm -qa | grep jdk
#卸载内置的JDK
yum remove java-1.6.0-openjdk
yum remove java-1.7.0-openjdk

```

### 查看系统是否安装了wget版本软件

[离线下载wget](http://mirrors.163.com/centos/7.2.1511/os/x86_64/Packages/wget-1.14-10.el7_0.1.x86_64.rpm)

```java
// 输入wget
wget： missing URL
// 安装 wget命令
yum install wget
// 安装
rpm -ivh wget-1.14-10.el7_0.1.x86_64.rpm
```

### 下载java8 

安装RPM

```java
// 在线在linux终端下载RPM
wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "http://download.oracle.com/otn-pub/java/jdk/8u91-b14/jdk-8u91-linux-x64.rpm"
```

[网页离线下载RPM，然后上传linux服务器安装](http://download.oracle.com/otn-pub/java/jdk/8u91-b14/jdk-8u91-linux-x64.rpm?AuthParam=1462805862_8be369be38fdce92bf8162c929be817b)

```java
rpm -ivh jdk-8u91-linux-x64.rpm
// 测试java是否安装成功
java -version
```

### tar.gz安装

[在线下载tar.gz版本](http://download.oracle.com/otn-pub/java/jdk/8u91-b14/jdk-8u91-linux-x64.tar.gz?AuthParam=1462934736_6fb6b206c0b3018e3ad5642e2893687b)

### 上传解压安装

```java
# 上传解压
tar -zxvf jdk-8u91-linux-x64.tar.gz -C /opt/soft
```

### 修改配置环境

```java
# 修改配置文件
vi /etc/profile
# 在export PATH USER LOGNAME MAIL HOSTNAME HISTSIZE HISTCONTROL下添加

export JAVA_HOME=/opt/soft/jdk1.8.0_91
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar

# 刷新配置文件
source /etc/profile
```

### 安装Tomcat8

```java
// 下载
wget http://mirror.bit.edu.cn/apache/tomcat/tomcat-8/v8.0.33/bin/apache-tomcat-8.0.33.tar.gz
// 解压
tar -zxvf apache-tomcat-8.0.33.tar.gz -C /opt/soft
// 启动Tomcat
cd /opt/soft/apache-tomcat-8.0.33/bin/
./startup.sh
// 8080端口添加到防火墙例外并重启
firewall-cmd --zone=public --add-port=8080/tcp --permanent
firewall-cmd --reload
// 访问tomcat
localhost:8080
```

