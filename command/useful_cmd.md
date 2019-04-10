#### 一些有用的命令
+ `htop`: 方便地查看`CPU`与内存的使用情况
+ `watch`: `watch -n 1 nvidia-smi` 间隔1秒，实时检测显卡使用情况
+ `docker rmi $(docker images -f "dangling=true" -q)`: 删除none none 镜像
