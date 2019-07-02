#### Docker 使用X11服务运行gui程序的一些命令

##### 需要安装的东西

```shell
sudo apt-get install x11-xserver-utils
xhost + # 开放权限,允许所有用户包括docker访问X11显示接口
```

##### 具体操作

```shell
xhost + # 每次重启后都需要此操作赋予docker权限
docker run 
#附加选项
-v /tmp/.X11-unix:/tmp/.X11-unix \ #共享本地unix端口 
-e DISPLAY=unix$DISPLAY \ #修改docker的环境变量

```

##### 如何测试能否正常显示

```shell
sudo apt-get install xarclock # 安装小程序
xarclock
```

#### 完整一些的教程

目前Unix/Linux比较主流的图形界面服务是X11，而X11服务的图形显示方式实际上是一种Client/Server模式，在服务端和客户端之间，X11通过`DISPLAY`环境变量来指定将图形显示到何处。如下面的流程所示，请注意服务端与客户端的位置，服务端是用于提供显示信息的。[应用程序]->[X11客户端]->[X11服务端]->[显示屏幕].

##### `DISPLAY`变量

格式为: `unix:port` 或者 `主机名:port` 

前一种为使用本地unix套接字,后一种表示使用tcp套接字

默认情况下,X11服务端会监听本地`unit:0`端口,`DISPLAY`的默认值为`:0`实际上为`unit:0`的简写.因此如果在当前Linux的控制台启动一个应用程序,那么其会在当前主机的显示屏中显示.

##### Docker 运行可视化程序的原理

基本原理为通过某种方式把X11的客户端内容从容器中传递出来,思路无非两种:

+ 通过ssh连接或者远程控制软件,通过tcp套接字把数据发送出来
+ 让容器和主机共享X11的unix套接字

实际情况分为:

+ 运行在本地的GUI程序
+ 运行在远程服务器上的GUI程序

##### 实际操作

```shell
$ sudo apt-get install x11-xserver-utils

$ xhost +

$ docker run -d \

  -v /etc/localtime:/etc/localtime:ro \

  -v /tmp/.X11-unix:/tmp/.X11-unix \

  -e DISPLAY=unix$DISPLAY \

  -v $HOME/slides:/root/slides \

  -e GDK_SCALE \

  -e GDK_DPI_SCALE \ 
  
  --name libreoffice \

  jess/libreoffice

```

`远程服务器的情况`:

数据流: [应用程序]->[X11客户端]->[SSH服务端]->[SSH客户端]->[X11服务端]->[显示屏幕]

当使用ssh连接运行程序的时候,使用`ssh -X`参数,开启ssh的X11特性.

需要修改的地方有如下两处:

+ 设置环境变量`DISPLAY`,不能再是`unix$DISPLAY`了
+ `--net=host`开启服务器上的docker容器网络连接

`DISPLAY`的值:ssh连接后查看`DISPLAY`的值为:`localhost:10.0`主机的`localhost:10.0`映射到容器中就变成了`0.0.0.0:10.0`.可以简写为`:10.0`,X11首先会去寻找`unix:10.0`发现没有,之后会去尝试`0.0.0.0:10.0`.

修改后的启动命令为:

```shell
  $ docker run -d \

  -v /etc/localtime:/etc/localtime:ro \

  -v $HOME/.Xauthority:/root/.Xauthority \ #授权文件
  
  --net=host \

  -e DISPLAY=:10.0 \

  -v $HOME/slides:/root/slides \

  -e GDK_SCALE \

  -e GDK_DPI_SCALE \

  --name libreoffice \

  jess/libreoffice

```



