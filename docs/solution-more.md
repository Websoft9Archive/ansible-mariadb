# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

The data directory for MariaDB is set to /data/mysql by default. If you want to modify MariaDB Data Directory, following are the steps for you:


## Modify MariaDB Data Directory

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

## Set The Binary Log

The binary log contains "event" that describe database changes such as table creation operations or changes to table data. It also contains events for statements that potentially could have made changes (for example, a DELETE which matched no rows), unless row-based logging is used. The binary log also contains information about how long each statement took that updated data. 

### Binary log configuration

You can modify the MariaDB configuration _/etc/my.cnf_ to change the binary log settings<br />

```
log_bin = mysql-bin      # enable Binary log
binlog_format = mixed    # Binary log format
expire_logs_days = 7     # Binary log expire time
```

### Binary log file size
Some times, there a lot of event for your database, then the binary log file size very rapid growth and your disk space may not enough, if there no space on disk, your MariaDB Service can not start.

Suggest you change the expire_logs_day to more smaller if you binary log file size is too big

## Secure MariaDB

Once you have created a new database and user for your application, connect to your MariaDB server and follow these recommendations:

- Remove anonymous users:

```sql
mysql> DELETE FROM mysql.user WHERE User='';
```

- Remove the _test_ database and access to it:

```sql
mysql> DROP DATABASE test;
mysql> DELETE FROM mysql.db WHERE Db='test' OR Db='test\\_%';
```

- Disallow root login remotely:
```sql
mysql> DELETE FROM mysql.user WHERE User='root' AND Host NOT IN ('localhost', '127.0.0.1', '::1');
```

- Don't forget to reload the privileges tables to apply the changes:
```sql
mysql> FLUSH PRIVILEGES;
```

- Change your _root_ user password.
- It is strongly recommended that you do not have empty passwords for any user accounts when using the server for any production work.<br />
- If you don't need remote access, uncomment the line

```
#bind-address=127.0.0.1
```

- in the MariaDB configuration file to only listen for connections on the local machine. Restart the server once done.


> Prior to MariaDB 5.7, when you installed MariaDB, it included a test database by default. This database is only used for testing, but all users who can connect to MariaDB have almost all the permissions of the test library, so there are certain security risks. From an information security perspective, if you find that you have the test database in MariaDB, be sure to remove it.