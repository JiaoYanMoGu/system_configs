# nvidia-docker2

nvdia-docker2为机器学习提供了一个隔离的开发环境，能够减少各个程序对环境的依赖。

## 1. 安装前的需求

需要安装好docker-ce，请参考[安装Docker](install.md)

系统需求：
* GNU/Linux x86_64 with kernel version > 3.10
* Docker >= 1.12
* NVIDIA GPU with Architecture > Fermi (2.1)
* NVIDIA drivers ~= 361.93 (untested on older versions)

### 1.1 删除老版本的nvidia-docker 1.0
如果你的系统之前安装过nvidia-docker 1.0, 考虑到兼容性，需要将其删除。

Ubuntu distributions
```
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge nvidia-docker
```

CentOS distributions
```
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo yum remove nvidia-docker
```

## 2 安装nvidia-docker2
确保你的系统安装了正确版本的[Nvidia driver](https://github.com/NVIDIA/nvidia-docker/wiki/Frequently-Asked-Questions#how-do-i-install-the-nvidia-driver)。

如果你设置了`/etc/docker/daemon.json`文件，那么nvidia-docker2可能会覆盖这个文件。

### 2.1 设置软件源
***1) Ubuntu系统下源的设置***

Xenial x86_64 (LinuxMint 18)
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/amd64/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
```

Xenial ppc64le
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/ubuntu16.04/ppc64el/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
```

***2) Debian系统下源的设置***

Stretch x86_64
```
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/debian9/amd64/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update
```

***3) CentOS系统下源的设置***

RHEL7 x86_64
```
curl -s -L https://nvidia.github.io/nvidia-docker/centos7/x86_64/nvidia-docker.repo | \
  sudo tee /etc/yum.repos.d/nvidia-docker.repo
```

RHEL7 ppc64le
```
curl -s -L https://nvidia.github.io/nvidia-docker/centos7/ppc64le/nvidia-docker.repo | \
  sudo tee /etc/yum.repos.d/nvidia-docker.repo
```


### 2.2 安装

***1) Ubuntu distributions:***
Install the nvidia-docker2 package and reload the Docker daemon configuration:
```
sudo apt-get install nvidia-docker2
sudo pkill -SIGHUP dockerd
```

***2) CentOS distributions:***
Install the nvidia-docker2 package and reload the Docker daemon configuration:
```
sudo yum install nvidia-docker2
sudo pkill -SIGHUP dockerd
```

## 3 使用

`nvidia-docker` registers a new container runtime to the Docker daemon.
You must select the `nvidia` runtime when using `docker run`:
```
docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi
```


### 参考文档

* [nvidia-docker2官方文档](https://github.com/NVIDIA/nvidia-docker)
