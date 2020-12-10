# Initial Installation

If you have completed the MariaDB deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to allow the **TCP:3306**  and **TCP:9090** 
> **3306** port is for MariaDB remote connection, and **9090** port is for access to phpMyAdmin

## MariaDB Installation Wizard

### Check MariaDB

1. Use the **SFTP** and **SSH** to connect Server, and run these command below to view the installation information and running status
   ```
   sudo systemctl status mariadb
   ```
2. You can ge the message from SSH " Active: active (running)... " when MariaDB is running

3. Then, you can get the guide of MariaDB
   ```
   man mariadb
   ```

Then, you can login MariaDB 

### Connect MariaDB

#### Connect MariaDB with commands

1. Using SSH to connect MariaDB Server(or remote to Windows Server), run the following command
   ~~~
   # get the root password of MariaDB
   sudo cat /credentials/password.txt

   # Login to MariaDB
   mariadb -uroot –p
   ~~~

2. You can see the following message when connection is successful
   ```
   Welcome to the MariaDB monitor.  Commands end with ; or \g.
   Your MariaDB connection id is 14
   Server version: 10.4.17-MariaDB MariaDB Server
   Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
   Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
   MariaDB [(none)]>
   ```

#### Login MariaDB with phpMyAdmin

If you used the deployment solution included the phpMyAdmin, the database management is very easy

1. Using local Chrome or Firefox to visit the URL *http://Internet IP:9090* to visit phpMyAdmin
  ![login phpMyAdmin](https://libs.websoft9.com/Websoft9/DocsPicture/en/mysql/mysql-login-websoft9.png)

2. Input your database account([Don't know password?](/stack-accounts.md#mysql))

3. Start using phpMyAdmin to modify root password of MariaDB
  ![phpMyAdmin](http://libs.websoft9.com/Websoft9/DocsPicture/en/phpmyadmin/phpmyadmin-changepwds-websoft9.png)

> More useful phpMyAdmin guide, please refer to [phpMyAdmin chapter](/solution-phpmyadmin.md) of this documentation



## Q&A

#### I can't visit the phpMyAdmin?

Your TCP:9090 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### How phpMyAdmin installed?

Install phpMyadmin used Docker, that can make sure MariaDB environment has good isolation
