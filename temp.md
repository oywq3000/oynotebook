hmall需要的docker容器

# hm_mysql

```
docker run \
--restart always \
-p 3307:3306 \
--name hm_mysql \
--privileged=true \
-v ~/dockerio/hm_mysql/conf:/etc/mysql/conf.d \
-v ~/dockerio/hm_mysql/logs:/logs \
-v ~/dockerio/hm_mysql/data:/var/lib/mysql \
-v ~/dockerio/hm_mysql/init:/docker-entrypoint-initdb.d \
-e TZ=Asia/Shanghai \
-e MYSQL_ROOT_PASSWORD=123456 \
-d mysql:8
```

其中~/dockerio/hm_mysql/conf有一hm.cnf文件内容如下

```
[client]
default_character_set=utf8mb4
[mysql]
default_character_set=utf8mb4
[mysqld]
character_set_server=utf8mb4
collation_server=utf8mb4_unicode_ci
init_connect='SET NAMES utf8mb4'

```

# nacos-hm

```

```

docker run -p 3306:3306 --name mysql 
-v /mydata/mysql/log:/var/log/mysql 
-v /mydata/mysql/data:/var/lib/mysql 
-e MYSQL_ROOT_PASSWORD=root  
-d mysql:5.7


# Oauth

clientID:`Ov23lihadb5gFGTSUnp0`

clientSecret:6ad2bae1c36128e4ac81f2661c49134df8dd9429
