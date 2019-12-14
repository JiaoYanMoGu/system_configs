## 速度挺快的VPS
Hostwinds /Vultr也行贵一些
> ubuntu 18.04已经自动开启了bbr加速，配置文件在/etc/sysctl.conf最后两行
## Shadowsocks 配置
```bash
sudo apt install python3-pip
apt-get install setuptools
pip3 install https://github.com/shadowsocks/shadowsocks/archive/master.zip
ssserver --version
```
创建配置文件:
```json
{
    "server":"my_server_ip",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"mypassword",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false
}
```
启动服务
```bash
ssserver -c ./ss.json -d start /restart

### 问题
+ ``pip: unsupported locale setting``:export LC_ALL=C
