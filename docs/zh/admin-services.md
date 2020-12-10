# 服务启停

使用由 Websoft9 提供的 MariaDB 部署方案，可能需要用到的服务如下：

## Linux系统

### MariaDB
```shell
sudo systemctl start mariadb
sudo systemctl stop mariadb
sudo systemctl restart mariadb
sudo systemctl status mariadb
```

### Docker

```shell
sudo systemctl start docker
sudo systemctl restart docker
sudo systemctl stop docker
sudo systemctl status docker
```

## Windows 系统

Windows下的镜像采用操作系统的服务管理功能，来实现 MariaDB 的启动、停止和重启操作
![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/mysql-servicewin-websoft9.png)