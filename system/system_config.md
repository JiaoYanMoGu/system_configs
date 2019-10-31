### 系统配置文档

#### 一、shadowsocket-qt5

```bash
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5
# 选择http而不是socket5
```

#### 二、Latex配置

```bash
sudo apt-get install texlive-full
sudo apt-get install texlive-publishers
官网下载最新版本TexStudio
IEEE模板问题:sudo apt-get install texlive-fonts-recommended
```

#### 三、脚本自动输入密码

```bash
echo '123' | sudo -S 命令
```

#### 四、OpenCV 3编译

```bash
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_TBB=ON -D WITH_V4L=ON -D WITH_QT=ON -D WITH_OPENGL=ON ..
# 手动下载ippicv这个压缩文件，放在opencv-3.1.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e
```

#### 五、Ctrl + Alt + A截图
系统，键盘设置，快捷键中添加命令`gnome-screenshot -a`为自定义快捷键即可. 


#### Clion + ROS

```bash
cd ~/.local/share/applications
vim  jetbrains-clion.desktop
添加"bash -i -c "
```

#### Mount server
```bash
sudo mkdir /mnt/data
sudo mount -t cifs -o username=a409,password=a409 -l //192.168.1.4/data /mnt/data 
```

#### Fast Github
```bash
nslookup github.com
nslookup github.global.ssl.fastly.net
# add to /etc/hosts and /etc/init.d/networking restart
```

#### Ubuntu 18.04 Docker 
查看系统发行版本
```bash
lsb_release -a
```
安装依赖
```bash
sudo apt install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

添加存储库(nightly)
如需要:`stable`更改对应配置即可
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
echo "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic nightly" > /etc/apt/sources.list.d/docker-nightly.list
```
更新仓库并安装
```bash
sudo apt update
sudo apt search docker-ce
sudo apt install docker-ce
```
启动并使其每次随系统启动
```bash
systemctl start docker
systemctl enable docker 
```
用户添加到Docker组
```bash
usrmod -aG docker xl # 你的用户名
```
配置国内代理以及设置docker存储位置，参考之前脚本

#### pdftk安装
```bash
sudo add-apt-repository ppa:malteworld/ppa
sudo apt update
sudo apt install pdftk
```
