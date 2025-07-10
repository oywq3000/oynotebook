# Docker环境安装

1.安装yum-utils

```
yum install -y yum-utils device-mapper-persistent-data lvm2
```

2.为yum源添加docker仓库位置

```
yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

3.安装docker服务

```
yum install docker-ce
```

4.启动docker服务

```
systemctl start docker
```

5.设置开机自启

```
systemctl enable docker
```
