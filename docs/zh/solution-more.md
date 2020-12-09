# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 更换MariaDB数据目录

The data directory for MariaDB is set to */data/mysql* by default. If you want to modify MariaDB Data Directory, following are the steps for you:

1. Stop the MariaDB Service
   ```shell
   sudo sytemctl stop mysqld
   ```
2. Move the */data/mysql* to the destination directory, e.g */data/mysql2* 
3. Modify the location of this folder modifying the`/etc/my.cnf` file, as shown below:
   ```shell
   datadir=/data/mysql2
   ```
4. Restart the MariaDB
   ```shell
   sudo sytemctl start mysqld
   ```


## 设置 Binary Log

The binary log contains "event" that describe database changes such as table creation operations or changes to table data. It also contains events for statements that potentially could have made changes (for example, a DELETE which matched no rows), unless row-based logging is used. The binary log also contains information about how long each statement took that updated data. 

### Binary log configuration

You can modify the MariaDB configuration _/etc/my.cnf_ to change the binary log settings

```
log_bin = mysql-bin      # enable Binary log
binlog_format = mixed    # Binary log format
expire_logs_days = 7     # Binary log expire time
```

### Binary log file size
Some times, there a lot of event for your database, then the binary log file size very rapid growth and your disk space may not enough, if there no space on disk, your MariaDB Service can not start.

Suggest you change the expire_logs_day to more smaller if you binary log file size is too big

## 权限设置

待续...

## 重置密码

常用的 MariaDB 重置密码相关的操作主要有修改密码和找回密码两种类型：

### 修改密码

可以通过 MariaDB 可视化管理工具修改密码，也通过命令行修改密码

* 通过 phpMyAdmin 修改密码
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-modifymysqlpw.gif)

* 通过命令行修改密码
   ```
   mysqladmin -u 用户名 -p 旧密码 password '新密码' 
   ```

### 找回密码

如果忘记了 root 密码，就需要通过命令操作，实现MariaDB密码重置。  

为了用户使用方便，我们已经将 MariaDB 重置密码写成脚本，使用只需两步：

1. 使用SSH远程连接到 MariaDB 服务器
2. 运行如下命令，按提示输入新密码即可。
   ```
   sudo su -
   wget -N https://raw.githubusercontent.com/websoft9dev/role_mariadb/master/tools/reset_password.sh; bash reset_password.sh
   ```