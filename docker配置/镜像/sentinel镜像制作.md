1. 创建Dockerfile文件

```
# 使用官方 Java 8 基础镜像
FROM openjdk:8-jdk-alpine

# 设置工作目录
WORKDIR /app

# 复制 Sentinel Dashboard JAR 文件到镜像中
COPY sentinel-dashboard.jar /app/sentinel-dashboard.jar

# 暴露端口 (默认 8080 + 自定义的 8090)
EXPOSE 8080 8090

# 设置启动命令 (使用环境变量允许动态配置)
CMD java ${JAVA_OPTS} \
    -Dserver.port=${SERVER_PORT:-8080} \
    -Dcsp.sentinel.dashboard.server=${DASHBOARD_SERVER:-localhost}:${SERVER_PORT:-8080} \
    -Dproject.name=sentinel-dashboard \
    -jar sentinel-dashboard.jar
```

2.构建Docker镜像

```
docker build -t sentinel-dashboard:1.8.6 .
```

3.运行Docker容器

```
docker run -d --name sentinel \
  -p 8090:8090 \
  -e SERVER_PORT=8090 \
  -e DASHBOARD_SERVER=localhost \
  --restart=always \
  sentinel-dashboard:1.8.6
```


1. **`-p 8090:8090`**
   将主机的 8090 端口映射到容器的 8090 端口
2. **`-e SERVER_PORT=8090`**
   设置容器内应用运行端口
3. **`-e DASHBOARD_SERVER`** (重要!)
   必须设置为 **宿主机对外的 IP 地址** 或  **域名** ，这是为了让其他 Sentinel 客户端能正确连接到 Dashboard

4.使用Dcoker Compose

```
version: '3'
services:
  sentinel-dashboard:
    image: sentinel-dashboard:1.8.6
    container_name: sentinel
    ports:
      - "8090:8090"
    environment:
      - SERVER_PORT=8090
      - DASHBOARD_SERVER=your_host_ip  # 替换为实际主机IP
    restart: always
```
