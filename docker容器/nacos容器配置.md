# docker部署配置

## 1.x版本

```
docker run --env MODE=standalone --name nacos --restart=always -d -p 8848:8848 nacos/nacos-server:1.2.0
```

## 2.x版本

2.1拉取对应镜像：docker pull nacos/nacos-server:2.0.2

2.2在数距库中持久化保存nacos配置信息，创建如下database

配置文件：[nacos.sql](/docker容器/配置文件/docker容器配置文件/nacos.sql),执行该sql脚本创建对应的数距库

2.3编写环境配置文件
配置文件：[custom.env](/docker容器/配置文件/docker容器配置文件/custom.env) ，配置好具体的sql地址密码等待

执行如下run命令：

```
docker run -d \
--name nacos-hm \
--env-file ./custom.env \
-p 8849:8848 \
-p 9848:9848 \
-p 9849:9849 \
--restart=always \
--network hm_net \
nacos/nacos-server:

```

# 服务注册

服务注册步骤如下：

```
 <dependency>
      <groupId>com.alibaba.cloud</groupId>
      <artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
 </dependency>
```

# 服务发现

```
 private final DiscoveryClient discoveryClient;
 private void handleCartItems(List<CartVO> vos) {
        //1.根据服务名，拉取服务的实例列表
        List<ServiceInstance> instances = discoveryClient.getInstances("item-service");
        //2.负载均衡，挑选一个实例
        ServiceInstance instance = instances.get(RandomUtil.randomInt(instances.size()));
        //3.获取实例的IP和端口
        URI uri = instance.getUri();
        //...略
}
```
