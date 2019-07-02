### ubuntu 16.04 搭建samba文件服务器
1. 安装samba samba-common
```shell
sudo apt-get install samba samba-common
```

2. 创建共享目录
```shell
sudo mkdir /home/dell/pi-lab
```

3. 更改权限所有人可读可写可执行
```shell
sudo chmod 777 /home/dell/pi-lab
```

4. 更改配置文件
`/etc/samba/smb.conf`
```shell
log file = .....

max_log_size = 1000

# 说明需要输入账号和密码才可以访问
security = user
```
文件尾部添加
```shell
[myshare] # 这个是你mount时候指定的名字,即共享目录对外名称
comment = my share directory #注释
path = /home/dell/pi-lab #共享的文件夹

browseable = yes
writeable = yes
```
保存

5. 设置密码
```shell
sudo smbpasswd -a a409 #a409为用户名
#输入密码即可
```

6. 重启smb服务
```shell 
sudo service smbd restart
```

### 挂载远程服务器
```shell
sudo mount -t cifs -o username=a409,password=a409,uid=1000,gid=1000 //10.168.39.173/myshare /mnt/pi-lab
```
