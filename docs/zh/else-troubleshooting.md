# 故障处理

此处收集使用 MariaDB 过程中最常见的故障，供您参考

> 大部分故障与云平台密切相关，如果你可以确认故障的原因是云平台造成的，请参考[云平台文档](https://support.websoft9.com/docs/faq/zh/tech-instance.html)

#### 导入数据库报错？

查看脚本里面是否有创建数据库的脚本

#### 数据库服务无法启动

数据库服务无法启动最常见的问题包括：磁盘空间不足，内存不足，配置文件错误。  
建议先通过命令进行排查  

```shell
# 查看磁盘空间
df -lh

# 查看内存使用
free -lh

# 查看数据库日志
cat /data/mariadb/mariadb.err
```

#### 数据库日志文件太大，导致磁盘空间不足？

默认安装，mysql会自动开启binlog，binlog是一个二进制格式的文件，用于记录用户对数据库**更新的****SQL语句****信息**，例如更改数据库表和更改内容的SQL语句都会记录到binlog里。

binlog主要用于出现没有备份的情况下，恢复数据库。但binlog会占用较大空间，长期不清理会让剩余磁盘空间为0，从而影响数据库或服务器无法启动

如果对自己的备份有信心，不需要binlog功能，参考如下步骤关闭之：

1. 编辑 [MariaDB 配置文件](/zh/stack-components.md#mariadb)，注释掉 binlog 日志
  ~~~
  #log-bin=mysql-bin  
  ~~~
2. 重启 MySQL 服务
  ~~~
  sudo systemctl restart mariadb
  ~~~

#### MariaDB 容器无法远程访问？

导致这个问题的可能原因有三点：

1. 端口映射设置错误，导致容器没有网络
2. 容器没有开启远程访问权限
3. MariaDB 某些版本的特殊要求

#### mysqladmin 修改普通用户密码 "Access denied; you need the SUPER privilege for this operation"？

原因：mysqlamdin 命令需 SUPER 权限，而普通用户默认没有这个权限。  
方案：使用 `set password=password("newpassword")` 命令修改密码

#### 一次性删除指定数据库中的所有表为什么难以成功？

数据表之间的**外键约束**导致有些数据表无法删除

#### 数据库出现死锁？

死锁一般是应用程序设计问题导致，其中事务操作出现死锁的几率更大。  

一旦出现死锁，可以用如下命令确认死锁的原因：

```
MariaDB [(none)]> show innodb status \G;
```



