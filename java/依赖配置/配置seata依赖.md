# 依赖引入

```
<dependency>
            <groupId>com.alibaba.cloud</groupId>
            <artifactId>spring-cloud-starter-alibaba-seata</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>io.seata</groupId>
                    <artifactId>seata-spring-boot-starter</artifactId>
                </exclusion>
            </exclusions>
        </dependency>
        <dependency>
            <groupId>io.seata</groupId>
            <artifactId>seata-spring-boot-starter</artifactId>
            <version>${seata.version}</version>
        </dependency>
```

其中seat.version在父工程中配置

# 配置application.yml文件

```yaml
seata:
  registry:
    type: nacos
    nacos:
      server-addr: 192.168.200.130:8848
      namespace: ""
      group: SEATA_GROUP
      application: seata-server
  tx-service-group: seata-demo #事物组名称
  service:
    vgroup-mapping: #事物组与cluster的映射关系
      seata-demo: default
```

nacos服务名称组包括：

- namespace+group+serviceName+cluster

seata客户端获取tc的cluster名称方式：

- 以tx-group-service的值为key到vgroupMapping中查找
