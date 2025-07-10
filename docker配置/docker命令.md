# 导入镜像

```
docker load -i /path/to/your-image.tar
```

# 自定义Docker ps

```
alias dps='docker ps --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"'
```

```
alias dpsa='docker ps -a --format "table {{.ID}}\t{{.Names}}\t{{.Status}}\t{{.Ports}}"'
```

运行 `source ~/.bashrc` 后，直接输入 `dps` 即可使用精简输出。

# 修改容器配置参数

```
docker update --restart=always <容器id或名子>
```

# 改变和查看文件夹访问模式

```
chmod 777 /root/app/mall-swarm/elasticsearch/data
```

```
ls -ld /path/to/your/directory
```
