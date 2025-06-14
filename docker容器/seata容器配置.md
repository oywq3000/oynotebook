# 基础安装

run镜像：

```
$ docker run --name seata-server \
	--restart always \
        -p 8091:8091 \
        -p 7091:7091 \
        -e SEATA_CONFIG_NAME=file:/root/seata-config/registry \
        -v /PATH/TO/CONFIG_FILE:/root/seata-config  \
        seataio/seata-server

```

示例：

```bash
docker run --name seata-server \
    --restart always \
    -p 8091:8091 \
    -p 7091:7091 \
    -e SEATA_CONFIG_NAME=file:/root/seata-config/registry \
    -v /root/dockerio/seata/seata-config:/root/seata-config \
    -d seataio/seata-server:1.6.0
```

registry.conf文件

```
registry {
	type = "nacos"

	nacos {
		application = "seata-tc-server"
		serverAddr = "nacos:8848"
		group = "DEFAULT_GROUP"
		namespace = ""
		cluster = "SH" 
		username = "nacos"
		password = "nacos"

	}
}

config {

	type = "nacos"

	nacos {
		serverAddr = "nacos:8848"
		namespace = ""
		group = "SEATA_GROUP"
		username = "nacos"
		password = "nacos"
		dataId = "seataServer.properties"

	}

}
```

nacos 服务器上的配置文件seataServer.properties

```bash
store.mode=db
store.db.datasource=druid
store.db.dbType=mysql
store.db.driverClassName=com.mysql.jdbc.Driver
store.db.url=jdbc:mysql://mysql:3306/seata?useUnicode=true&rewriteBatchedStatements=true
store.db.user=root
store.db.password=123456
store.db.minConn=5
store.db.maxConn=30
store.db.globalTable=global_table
store.db.branchTable=branch_table
store.db.queryLimit=100
store.db.lockTable=lock_table
store.db.maxWait=5000
# 事务、日志等配置将
server.recovery.committingRetryPeriod=1000
server.recovery.asynCommittingRetryPeriod=1000
server.recovery.rollbackingRetryPeriod=1000
server.recovery.timeoutRetryPeriod=1000
server.maxCommitRetryTimeout=-1
server.maxRollbackRetryTimeout=-1
server.rollbackRetryTimeoutUnlockEnable=false
server.undo.logSaveDays=7
server.undo.logDeletePeriod=86400000
# 客户端与服务端传输方式
transport.serialization=seata
transport.compressor=none
# 关闭metrics功能，提高性能
metrics.enabled=false
metrics.registryType=compact
metrics.exporterList=prometheus
metrics.exporterPrometheusPort=9898
```
