# Docker

标签（空格分隔）： SummerCamp2018 Docker

---

[toc]

## 1. 概述

由于开发机器学习和视觉，需要配置比较多的库，因此使用docker能够将配置的环境打包到docker image，并利用局域网的registry服务器，能够快速在另外一台电脑运行配置好的环境，从而极大的提高工作效率。如果想了解更多关于docker、以及它的背景，可以查看[docker简介](content/about_docker.md)


## 2. 学习目标与学习方法
### 2.1. 目标
　　掌握Docker的基本用法，能够熟练的打包镜像，运行。

### 2.2. 方法
　　推荐读者根据本教程内容的步骤进行操作，同时浏览推荐的学习资料，如有任何不清楚的地方可参考推荐的学习资料或者自行搜索答案和找他人解答。
　　

## 3. 课程内容

一步一步学习docker
* [安装Docker](content/install.md)
* [安装后的准备工作](content/prepare.md)
* [获取镜像](content/pull.md)
* [操作容器](content/container.md)
* [使用Dockerfile](content/dockerfile.md)
* [操作仓库](content/push.md)
* [nvida-docker2](content/nvidia-docker2.md)
* [docker registry](content/docker_registry.md)


docker常用的命令
* [docker常用命令与概念](content/docker_commands.md)

## 4. Docker的工具
可以下载docker常用工具和命令，简化docker的安装和使用，代码的下载地址是： http://192.168.1.3/PI_LAB/docker_scripts

这个工具集包括：
* 自动下载安装`docker`, `nvidia-docker2`
* 制作、运行、pull/push到实验室的registry服务器
* 安装操作系统，常用工具的脚本等



## 5.　课程作业

**目标：** 使用Dockerfile构建镜像编译[GSLAM](https://github.com/zdzhaoyong/GSLAM)，并使用docker run命令运行gslam, 导出镜像到文件gslam_<yourname>.tar, 并将Dockerfile文件和镜像文件提交到Report/tool/docker/<yourname>目录中。


## 6. 参考资料，教程等

* [Docker — 从入门到实践]( https://yeasy.gitbooks.io/docker_practice)
* [自己学Docker](http://blog.csdn.net/Mungo/article/category/6183705)
* [Container Hacks and Fun Images](https://pan.baidu.com/s/1bn0hdpH)
* [Docker核心概念、安装、端口映射及常用操作命令](https://www.toutiao.com/a6587930586013237763)
* [Docker入门教程](https://www.toutiao.com/a6531975282004328963/)
* [Docker command line references](https://docs.docker.com/engine/reference/commandline/docker/)
