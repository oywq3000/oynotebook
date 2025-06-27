docker run 
--restart always 
--network hm_net 
-p 3307:3306 
--name hm_mysql 
--privileged=true 
-v ~/dockerio/hm_mysql/conf:/etc/mysql/conf.d 
-v ~/dockerio/hm_mysql/logs:/logs 
-v ~/dockerio/hm_mysql/data:/var/lib/mysql 
-v ~/dockerio/hm_mysql/init:/docker-entrypoint-initdb.d 
-e TZ=Asia/Shanghai 
-e MYSQL_ROOT_PASSWORD=123456 
-d mysql:8

docker run --name seata-server-hm \
    --restart always \
    --network hm_net \
    -p 8099:8099 \
    -p 7099:7099 \
    -v /root/dockerio/seata/seata-config/resources-hm:/seata-server/resources \
    -e SEATA_IP=192.168.200.130 \
    -d seataio/seata-server:1.6.0
