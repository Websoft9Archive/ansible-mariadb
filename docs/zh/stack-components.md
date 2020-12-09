# 参数

MariaDB 预装包包含 MariaDB 运行所需一序列支撑软件（简称为“组件”），下面列出主要组件名称、安装路径、配置文件地址、端口、版本等重要的信息。

## 路径

MariaDB 安装到 Linux 还是 Windows 系统，对应的路径有很大的差异，请根据实际情况参考：

### Linux

#### MariaDB

MariaDB 配置文件: */etc/my.cnf*   
MariaDB 数据目录：*/data/mariadb*   
MariaDB 错误日志: */data/mariadb/mariadb.err*  
MariaDB Socket: */data/mariadb/mariadb.sock*

#### phpMyAdmin

phpMyAdmin 是一款可视化 MySQL 管理工具，在本项目中它基于 Docker 安装。  

phpMyAdmin directory：*/data/apps/phpmyadmin*  
phpMyAdmin docker compose file：*/data/apps/phpmyadmin/docker-compose.yml* 

### Windows

* 目录：C:/websoft9/mariadb
* 配置文件：C:/websoft9/mariadb/etc/my.ini
* 数据文件目录:：C:/websoft9/mariadb/data

## 端口号

在云服务器中，通过 **[安全组设置](https://support.websoft9.com/docs/faq/zh/tech-instance.html)** 来控制（开启或关闭）端口是否可以被外部访问。 

通过命令`netstat -tunlp` 看查看相关端口，下面列出可能要用到的端口：

| 名称 | 端口号 | 用途 |  必要性 |
| --- | --- | --- | --- |
| phpMyAdmin on Docker | 9090 | 通过 HTTP 访问 phpMyAdmin | 可选 |
| MariaDB | 3306 | 远程连接 MariaDB | 可选 |

## 版本号

组件版本号可以通过云市场商品页面查看。但部署到您的服务器之后，组件会自动进行更新导致版本号有一定的变化，故精准的版本号请通过在服务器上运行命令查看：

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