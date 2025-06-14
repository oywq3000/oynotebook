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


[
    {
        "Id": "6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792",
        "Created": "2025-06-13T07:43:11.320927398Z",
        "Path": "docker-entrypoint.sh",
        "Args": [
            "mysqld"
        ],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 46919,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2025-06-14T02:11:06.07354033Z",
            "FinishedAt": "2025-06-14T02:09:32.49578044Z"
        },
        "Image": "sha256:8f360cd2e6e4a37e8b8638fec65c779e4c1c1f4f785765bf2aab3fbc59f95a26",
        "ResolvConfPath": "/var/lib/docker/containers/6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792/hostname",
        "HostsPath": "/var/lib/docker/containers/6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792/hosts",
        "LogPath": "/var/lib/docker/containers/6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792/6f9c32c20ffa24b44e6fa65662b3b638d8e5ece781ce328986587c4bdcf0f792-json.log",
        "Name": "/mysql",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": [
                "/root/dockerio/mysql/conf/my.cnf:/etc/mysql/my.cnf",
                "/root/dockerio/mysql/logs:/logs",
                "/root/dockerio/mysql/data:/var/lib/mysql"
            ],
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {
                "3306/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "3306"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "always",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "CapAdd": null,
            "CapDrop": null,
            "Capabilities": null,
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": true,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": [
                "label=disable"
            ],
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "ConsoleSize": [
                0,
                0
            ],
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": null,
            "BlkioDeviceWriteBps": null,
            "BlkioDeviceReadIOps": null,
            "BlkioDeviceWriteIOps": null,
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "KernelMemory": 0,
            "KernelMemoryTCP": 0,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": null,
            "ReadonlyPaths": null
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/22285eadb0b4460433f4473dc18233937427e16cfe6ac689ce6646ebfe6dff48-init/diff:/var/lib/docker/overlay2/1a92265220b5283e1468ebed93e2ae6b4a9f9d24ec628d9a892646acc61981f9/diff:/var/lib/docker/overlay2/cc82fc3431588a83090c185f847a1970e13d221c5db83fcda323b578dd536168/diff:/var/lib/docker/overlay2/80764ebb169f7fa8efcfddf2809209b159dbce86cca43088ee85a2313073ec21/diff:/var/lib/docker/overlay2/418c43a4e1e1f67b3824d83e870b68a9aa68d2c6d0b1b4e02120648456cb04f8/diff:/var/lib/docker/overlay2/2bad892cfe6b6283f567f3e8a293e7c99c4ce2a69c36d8e0033bff5f42525d95/diff:/var/lib/docker/overlay2/20febc13f89879099693eb3f3b9cab383edb12a22d7d46a3a98394557493ee91/diff:/var/lib/docker/overlay2/5f578a4f665de0dbbc13797fd93e6e3f73c35583c2993fe4e745de2417f9d49e/diff:/var/lib/docker/overlay2/de983f67f7326e4bba8529aa67fd5413bba09eec14fcf64683cdddb21ab7e674/diff:/var/lib/docker/overlay2/27425ccc107cb8a7720da837f03c1511361fbce20dcb5b4c72056eb06b5646de/diff:/var/lib/docker/overlay2/04b2a0438823ef2778cf3016f16bf34ec6a7eae20fa0d98906cd619cea90c230/diff",
                "MergedDir": "/var/lib/docker/overlay2/22285eadb0b4460433f4473dc18233937427e16cfe6ac689ce6646ebfe6dff48/merged",
                "UpperDir": "/var/lib/docker/overlay2/22285eadb0b4460433f4473dc18233937427e16cfe6ac689ce6646ebfe6dff48/diff",
                "WorkDir": "/var/lib/docker/overlay2/22285eadb0b4460433f4473dc18233937427e16cfe6ac689ce6646ebfe6dff48/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [
            {
                "Type": "bind",
                "Source": "/root/dockerio/mysql/conf/my.cnf",
                "Destination": "/etc/mysql/my.cnf",
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            },
            {
                "Type": "bind",
                "Source": "/root/dockerio/mysql/logs",
                "Destination": "/logs",
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            },
            {
                "Type": "bind",
                "Source": "/root/dockerio/mysql/data",
                "Destination": "/var/lib/mysql",
                "Mode": "",
                "RW": true,
                "Propagation": "rprivate"
            }
        ],
        "Config": {
            "Hostname": "6f9c32c20ffa",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "3306/tcp": {},
                "33060/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "TZ=Asia/Shanghai",
                "MYSQL_ROOT_PASSWORD=123456",
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "GOSU_VERSION=1.17",
                "MYSQL_MAJOR=8.4",
                "MYSQL_VERSION=8.4.5-1.el9",
                "MYSQL_SHELL_VERSION=8.4.5-1.el9"
            ],
            "Cmd": [
                "mysqld"
            ],
            "Image": "mysql:8",
            "Volumes": {
                "/var/lib/mysql": {}
            },
            "WorkingDir": "/",
            "Entrypoint": [
                "docker-entrypoint.sh"
            ],
            "OnBuild": null,
            "Labels": {}
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "a9ce56737d83b1f8042aba9e39bdda8f267be7f1f4abb8c76d0bf7e8f10a0554",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "3306/tcp": [
                    {
                        "HostIp": "0.0.0.0",
                        "HostPort": "3306"
                    }
                ],
                "33060/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/a9ce56737d83",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "3f6507717a18ef5077e1a77d6d2d16efdff7bc608203a9a404867e08b8a1f2a4",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.5",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:05",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "d2ad02687ec22a4846e7f07f24c8348d037faa9d0c45fc37d29c7de277fe6b29",
                    "EndpointID": "3f6507717a18ef5077e1a77d6d2d16efdff7bc608203a9a404867e08b8a1f2a4",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.5",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:05",
                    "DriverOpts": null
                },
                "heads-net": {
                    "IPAMConfig": {},
                    "Links": null,
                    "Aliases": [
                        "6f9c32c20ffa"
                    ],
                    "NetworkID": "c5a624c3828c1d8f8996bed1b5ce29aeacfb7b0feacf8e2859808f680fc18232",
                    "EndpointID": "db29d7287d4062946cd59c9ca8758e85bc66fd151e1a6e4e205f42a53c6ff1d3",
                    "Gateway": "172.18.0.1",
                    "IPAddress": "172.18.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:12:00:02",
                    "DriverOpts": {}
                }
            }
        }
    }
]
