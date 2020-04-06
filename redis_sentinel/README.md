> redis.conf 为默认配置文件
> sentinel.conf 为默认配置文件

# 配置说明：

所有节点
注释了 bind 127.0.0.1
添加了 requirepass 123456

slave 节点配置：
replicaof 6.6.6.6:9001
masterauth 123456
replica-announce-ip 6.6.6.6
replica-announce-port 9011

sentinel 配置：
sentinel auth-pass mymaster 123456
sentinel announce-ip "6.6.6.6"
sentinel announce-port 29002

> announce 部分为 docker 环境 端口转发需要
>
> ip，port 请根据自己情况修改
