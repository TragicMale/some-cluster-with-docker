redis.conf 为默认配置文件

# 配置说明：

所有节点
注释了 bind 127.0.0.1
添加了 requirepass 123456

slave 节点配置：
replicaof
masterauth
