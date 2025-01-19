---
title: 树莓派安装Docker
date: 2025-01-18 18:55:49
tags:
  - Tech
  - Note
categoies:
  - Docker
---
# 树莓派安装Docker

{% note info%}此文章介绍在Raspberry Pi OS下安装Docker{% endnote %}

## 换源

更换清华镜像源
```bash
https://blog.csdn.net/qq_41676577/article/details/112856422
```
添加docker源
```bash
sudo add-apt-repository \
    "deb [arch=armhf] https://mirrors.aliyun.com/docker-ce/linux/raspbian \
    $(lsb_release -cs) \
    stable"
```

## 更新apt

```bash
sudo apt-get update | sudo apt-get upgrade
```

## 安装相关依赖

```bash
sudo apt-get install \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     lsb-release \
     software-properties-common
```

## 安装docker

### 手动安装

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

### 脚本自动安装

```bash
curl -fsSL get.docker.com -o get-docker.sh
sudo sh get-docker.sh --mirror Aliyun
```

## 将用户加入docker用户组【可选】

现在已经可以正常调用docker进行容器部署了，但是每次使用前都需要用sudo，为了避免麻烦可以将当前用户加入到docker的用户组中

```bash
sudo usermod -aG docker <username>
```

在运行完成上述命令之后，需要退出终端并重新登录，此时配置便可生效