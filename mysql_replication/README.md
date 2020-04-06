# master 配置

```mysql
create user 'replicator'@'%' identified by 'replicator';
grant replication slave on *.* to 'replicator'@'%'; -- %替换为slave IP

show master STATUS; -- 查看master状态
```

//查看容器 ip

```sh
docker inspect 容器 ID | grep IPAddress
```

# slave 配置

```mysql

-- flush tables with read lock; -- 全局锁，可以锁super用户
set global read_only=1; -- readonly 对super用户无效

change master to
master_host='172.25.0.2',
master_port=3306,
master_user='replicator',
master_password='replicator',
master_log_file='mysql-bin.000003',
master_log_pos=627;

start slave;

show slave status;
```
