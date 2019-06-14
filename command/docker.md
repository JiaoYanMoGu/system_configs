$ docker stop $(docker ps -a | grep "Exited" | awk '{print $1 }') //停止容器
$ docker rm $(docker ps -a | grep "Exited" | awk '{print $1 }')  //删除容器 
$ docker rmi $(docker images | grep "none" | awk '{print $3}')  //删除镜像 
