# Parameters

The MariaDB deployment package contains a sequence software (referred to as "components") required for MariaDB to run. The important information such as the component name, installation directory path, configuration file path, port, version, etc. are listed below.

## Path

You should know the components is different for different OS before using MariaDB

### Linux

#### MariaDB&MariaDB

MariaDB data directory: */data/mariadb*  
MariaDB configuration file: */etc/my.cnf*  
MariaDB error log: */data/mariadb/mariadb.err*  
MariaDB Socket: */data/mariadb/mariadb.sock*  

#### phpMyAdmin on Docker

phpMyAdmin is a visual MySQL management tool, is installed based on docker.  

phpMyAdmin directory：*/data/apps/phpmyadmin*  
phpMyAdmin docker compose file：*/data/apps/phpmyadmin/docker-compose.yml* 

### Windows Sever

Database install directory: */C:/websoft9/mysql*  
Database data directory: */C:/websoft9/mysql/data*  
Database configuration file: */C:/websoft9/mysql/my.ini*  


## Ports

Open or close ports by **[Security Group Setting](https://support.websoft9.com/docs/faq/tech-instance.html)** of your Cloud Server to decide whether the port can be accessed from Internet.  

You can run the cmd `netstat -tunlp` to check all related ports.  

The following are the ports you may use:

| Name | Number | Use |  Necessity |
| --- | --- | --- | --- |
| phpMyAdmin on Docker | 9090 | HTTP to visit phpMyAdmin | Optional |
| MariaDB | 3306 | remote connect MariaDB | Optional |

## Version

You can see the version from product page of Marketplace. However, after being deployed to your server, the components will be automatically updated, resulting in a certain change in the version number. Therefore, the exact version number should be viewed by running the command on the server:

```shell
# Check all components version
sudo cat /data/logs/install_version.txt

# Linux Version
lsb_release -a

# MariaDB version
MariaDB -V

# MariaDB Version
docker -v
```