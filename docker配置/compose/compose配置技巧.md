# 手动+工具编写Compose

1.手动收集配置信息

```
# 获取所有容器ID
docker ps -aq

# 针对每个容器导出配置（替换CONTAINER_ID）
docker inspect CONTAINER_ID > container_config.json
```

2.工具通过docker来拉取

```
docker pull ghcr.io/red5d/docker-autocompose:latest
```

对特定的容器：

```
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/red5d/docker-autocompose <container-name-or-id> <additional-names-or-ids>...  > hmall-compose.yml
```

对所有的容器：

```
docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/red5d/docker-autocompose $(docker ps -aq) > > hmall-compose.yml
```

3.确定好compose配置成功，删除对应的容器

```
# 停止并删除旧容器（确保备份数据！）
docker stop $(docker ps -aq) && docker rm $(docker ps -aq)
```

4.确保按照了docker-compose

```
# 创建插件目录
mkdir -p /usr/local/lib/docker/cli-plugins

# 下载并安装 Compose 插件（x86_64 架构）
curl -SL https://github.com/docker/compose/releases/download/v2.25.0/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose

# 授予执行权限
chmod +x /usr/local/lib/docker/cli-plugins/docker-compose

# 验证安装
docker compose version
```

4.启动compose项目

```
docker compose up -d
```

```
docker compose -f <文件路径> up -d
```

do
