# Ubuntu20.04更换阿里云镜像

[阿里云官方镜像站](https://developer.aliyun.com/mirror/)

### 具体方法如下:

#### 1. 备份系统自带的镜像源

```bash
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

#### 2. 打开/etc/apt/sources.list文件,并且添加一下条目

```java
// 可以使用vim,gedit,vi等编辑工具
sudo gedit /etc/apt/sources.list
// 添加阿里镜像源 20.04版本
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-security main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-proposed main restricted universe multiverse

deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
```

#### 3. 更新替换镜像源

```bash
sudo apt-get update
# 出现依赖问题,解决方式如下
sudo apt-get -f install
# 更新软件
sudo apt-get upgrade
```

