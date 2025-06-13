Mysql镜像配置

# 简单的run一个镜像操作

## 创建映射文件夹

```bash
mkdir -p ~/dockerio/mysql/data ~/dockerio/mysql/logs ~/dockerio/mysql/conf
`
- data目录将映射为mysql容器配置的数据文件存放路径

- logs目录将映射为mysql容器的日志目录

- conf目录里的配置文件将映射为mysql容器的配置文件

## my.cnf文件
 
```java
[mysqld]
# 网络配置
bind-address = 0.0.0.0
skip-name-resolve

# 连接设置
max_connections = 200
wait_timeout = 300

# 字符集配置
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci

# 性能优化
innodb_buffer_pool_size = 1G
innodb_log_file_size = 256M
# 日志配置
general_log = 0
slow_query_log = 1
long_query_time = 2
slow_query_log_file = /logs/slow-queries.log
```

## 实例化一个mysql镜像

```bash
docker run \
--restart always \
-p 3306:3306 \
--name mysql \
--privileged=true \
-v ~/dockerio/mysql/conf/my.cnf:/etc/mysql/my.cnf \
-v ~/dockerio/mysql/logs:/logs \
-v ~/dockerio/mysql/data:/var/lib/mysql \
-e TZ=Asia/Shanghai \
-e MYSQL_ROOT_PASSWORD=123456 \
-d mysql:8
```

## 设置远程连接用户

```sql
CREATE USER 'remote_user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'remote_user'@'%';
FLUSH PRIVILEGES;
```

# 远程连接命令

```bash
mysql -h <remote_server_ip> -u <username> -p
```
