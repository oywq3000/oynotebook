# 配置步骤：

```
$ docker search zookeeper # 查看一下镜像
 
$ docker pull zookeeper:3.4.9  # 拉取指定版本zk镜像
 
$ docker images  # 查看image ID
 
$ mkdir -p /root/docker/zookeeper/data
$ docker run -d -p 2181:2181 -v /yaxin/zookeeper/data:/data/ --name zookeeper --privileged zookeeper:3.8.0
```
