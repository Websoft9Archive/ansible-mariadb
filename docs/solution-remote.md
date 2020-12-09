# MariaDB remote connection

Most of the time, if you want to use GUI tools to manage MariaDB on you local computer, you shoud open the remote connection of MariaDB. 

Database is high security application, you need two steps for remote connection settings at least:

## Enable the TCP:3306 port

In general, MariaDB uses port 3306.

First, you must go to the Cloud Console and enable the **TCP:3306** port of Security Group
![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql3306-websoft9.png)


## Open MariaDB remote connection

After the security group is turned on, the setup of the MariaDB remote solution has not been completed.

Next, you need to set up MariaDB itself so that it can access external networks

We provide two solutions to open the remote connection of MariaDB. The first is GUI and the second is the command mode:

#### Use GUI(recommend)

To enable remote in phpMyAdmin, you only need to change the access mode of the root account to "any way to access", as follows:

1. Log in phpMyAdmin, go to User account->Edit privileges of root account
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/phpmyadmin/phpmyadmin-modifypw001-websoft9.png)

2. Select the tab Login Information, Host Name fill in "%", click "Go" button completing this setting
   ![](http://libs.websoft9.com/Websoft9/DocsPicture/en/phpmyadmin/phpmyadmin-modifypw002-websoft9.png)

#### Use commands

If you have not installed phpMyAdmin or other GUI tools in you Server, you should use command to open the MariaDB remote connection:

1. Use SSH to connect MariaDB Server
   ```
   sudo mysql -u root -p password
   ```
 
2. Open the remote connection
   ```
   mysql>  use mysql;
   mysql>  update user set host = '%' where user = 'root';
   ```

3. Test it
   ```
   select host,user from user where user='root'
   ```
4. Exit MariaDB command mode, return to Linux and restart it
   ```
   sudo systemctl restart mysqld
   ```
   > This step is necessary, otherwise Navicat Premium/MariaDB-Front can't connect to MariaDB