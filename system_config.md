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
