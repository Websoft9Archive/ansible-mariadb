
## MariaDB commands

Using SSH to connect to Linux or Windows-CMD of Remote Windows Server,then run the following command to connect MariaDB

### Connect MariaDB Server
~~~
mysql -u root –p
Enter password:

#exit mysql if you want
mysql> exit  
~~~

### Useful commands

The following are the most commonly used mysql command operations
```
#connect mysql as root,then input your password
mysql -u root -p

#show all databases
mysql> show  databases;

#delete the the database of dbname
mysql> drop database dbname;

#Create a new database
mysql> create database DATABASE_NAME;

#Create a new user (only with local access) and grant privileges to this user on the new database:
mysql> grant all privileges on DATABASE_NAME.* TO 'USER_NAME'@'localhost' identified by 'PASSWORD';

#Create a new user (with remote access) and grant privileges to this user on the new database
mysql> grant all privileges on DATABASE_NAME.* TO 'USER_NAME'@'%' identified by 'PASSWORD';

#exit the mysql mode
mysql> exit
```


## MariaDB GUI tools

Working on a relational database using only command line tools to writing queries can be hard, luckily we found the best Free GUI tools for your MariaDB work. Most uses of MariaDB for Web development allow you to get around a lot of back end requirements with the use of PHP and other tools that work the database without having to do more than set up. However, as the use of SQL for Web development has increased, and the complexities, so has the availability of tools to manage your SQL database. Here are some of the best tools for working with your MariaDB database.



| **Name**                                                     | **Description**                                              | **Cross platform**                            | **Price** |
| ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------------- | --------- |
| [MariaDB Workbench](https://dev.mysql.com/downloads/workbench/) | MariaDB Workbench is a unified visual tool for database architects, developers, and DBAs. MariaDB Workbench provides data modeling, SQL development, and comprehensive administration tools for server configuration, user administration, backup, and much more. | Windows,Linux,MacOS                           | Free      |
| [phpMyAdmin](https://www.phpmyadmin.net/)                    | phpMyAdmin is a free software tool written in PHP, intended to handle the administration of MariaDB over the Web. phpMyAdmin supports a wide range of operations on MariaDB and MariaDB. Frequently used operations (managing databases, tables, columns, relations, indexes, users, permissions, etc) can be performed via the user interface, while you still have the ability to directly execute any SQL statement. | Based on Web,one installation, use everywhere | Free      |
| [Navicat](https://www.navicat.com/en/products/navicat-for-mysql) | Navicat for MariaDB is the ideal solution for MariaDB administration and development. It is a single application that allows you to connect to MariaDB and MariaDB databases simultaneously. | Windows,MacOS,IOS                             | Not free  |
| [MariaDB-Front](http://www.mysqlfront.de/)                     | MariaDB-Front is a Windows front end program for the MariaDB database server. The database structure and data can be handled via dialogs or SQL commands. Import and Export in standard file formats is supported. The database server can be connected directly or via HTTP tunneling. | Windows                                       | Free      |
| [Sequel Pro](https://sequelpro.com/)                         | Sequel Pro is a fast, easy-to-use Mac database management application for working with MariaDB databases. | MacOS                                         | Free      |
| [HeidiSQL](https://www.heidisql.com/download.php)            | HeidiSQL is a useful and reliable tool designed for web developers using the popular MariaDB or MariaDB server, Microsoft SQL databases or PostgreSQL. Support for multiple languages (including Chinese) | Windows                                       | Free      |
| [DBeaver Community](https://dbeaver.io/)                     | Free multi-platform database tool for developers, SQL programmers, database administrators and analysts. Supports all popular databases: MariaDB, PostgreSQL, MariaDB, SQLite, Oracle, DB2, SQL Server, Sybase, MS Access, Teradata, Firebird, Derby, etc. | Windows                                       | Free      |
| [dbForge Studio for MariaDB Express](https://www.devart.com/dbforge/mysql/) | dbForge Studio for MariaDB is a universal GUI tool for MariaDB and MariaDB database development, management, and administration. The IDE allows you to create and execute queries, develop and debug stored routines, automate database object management, analyze table data via an intuitive interface. The MariaDB client delivers data and schema comparison and synchronization tools, database reporting tools, backup options with scheduling, and much more. | Windows                                       | Free      |



GUI tools gives you direct access to your MariaDB Databases on local and remote servers.
