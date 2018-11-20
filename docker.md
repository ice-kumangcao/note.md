[TOC]

##### docker 配置条件

+ [docker install](https://docs.docker.com/v1.7/docker/installation/centos/)
+ CentOS 7.X
+ CentOS 6.5 or higher
+ kernel 2.6.32-431 or higher

##### ~~ubuntu18.04 安装docker-io~~

````
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt install docker.io
````

##### docker 安装 portainer 管理工具

````shell
#访问地址http://localhost:9000
sudo docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
````

##### ~~docker 命令~~

```shell
docker pull mysql:5.6 # 拉取 MySQL5.6 的镜像
docker ps # 显示所有的正在运行的containers
docker ps -a # 显示所有的containers
docker start/stop containerid/containername # 运行/停止container
docker exec -it mysql bash # 连接运行的MySQL container
docker cp /home/ice/test.sql containerid:/home/ice/test.sql
```

