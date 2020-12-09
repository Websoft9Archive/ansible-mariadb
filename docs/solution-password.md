# Modify and reset MariaDB password

Modify password: Change the current password to another password  
Reset password: Have forgotten your password, need to get an initial password

## Modify password

You can modify password by MariaDB GUI or commands:

### Use phpMyAdmin(Recommend) 

![](http://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/websoft9-modifymysqlpw.gif)

### Use commands
```
mysqladmin -u root -p oldpassword password 'newpassword' 
```

## Reset password

You can reset your MariaDB password by the following two solution:  

### Quick Plan(Recommend) 

1. Use SSH to connect MariaDB Server
2. Run the following command
   ```
   sudo git clone https://github.com/Websoft9/linux.git; cd linuxscript/Mysql\_ResetPasswd\_Script;sudo sh reset\_mysql\_password.sh
   ```
### Manual solution

1. Use SSH to connect MariaDB Server
2. Stop MariaDB
   ~~~
   sudo systemctl stop mysqld
   ~~~
3. Use the safe mode to restart MariaDB
   ~~~
   sudo mysqld_safe --skip-grant-tables &
   ~~~
4. Reset password(e.g reset password to `123456`)
   ~~~
   sudo mysql -e "use mysql;update user set password=password('123456') where user='root';"
   ~~~
5. Shut down MariaDB service
   ~~~
   sudo kill all mysqld
   ~~~ 
6. Start MariaDB service
   ~~~
   sudo systemctl start mysqld
   ~~~