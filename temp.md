docker run -d 
--restart=unless-stopped 
--name seata-server 
-p 8091:8091 
-v /root/dockerio/seata/seata-server:/seata-server 
-e SEATA_IP=8091 
-e SEATA_PORT=8091 
seataio/seata-server:1.6.0

docker run --name seata-server 
    --restart always
    -p 8091:8091
    -p 7091:7091
    -e SEATA_CONFIG_NAME=file:/root/seata-config/registry
    -v /root/dockerio/seata/seata-config:/root/seata-config
    -d seataio/seata-server:1.6.0
