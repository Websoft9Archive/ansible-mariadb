# 初始化验证

在云服务器上部署 MariaDB 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:3306** 和 **TCP:9090** 端口是否开启

> 3306 端口用于远程连接 MariaDB，9090 端口用于访问 phpMyAdmin

## MariaDB 初始化验证

部署 MariaDB 之后，依次完成下面的步骤，验证其可用性

### 检测 MariaDB 安装

1. 使用 SSH 连接 MariaDB 所在的服务器，运行下面的命令，查看 MariaDB 的安装信息和运行状态
   ```
   sudo systemctl status mariadb
   ```
2. 运行服务状态查询命令，MariaDB 正常运行会得到 " Active: active (running)... " 的反馈

3. 镜像安装完成后，MariaDB就可以使用了。
   ```
   # 查看使用 MariaDB 使用手册
   man mariadb
   ```

### 连接 MariaDB

下面介绍命令行和可视化界面两种连接 MariaDB 的方式：

#### 命令方式连接 MariaDB

1. 使用 SFTP 或 SSH 客户端连接服务器，运行下面的命令：
   ```
   # 获取数据库密码
   cat /credentials/password.txt

   # 登录数据库，并输入密码后登录
   mariadb -uroot –p
   ```

2. 连接成功后显示的信息
   ```
   Welcome to the MariaDB monitor.  Commands end with ; or \g.
   Your MariaDB connection id is 14
   Server version: 10.4.17-MariaDB MariaDB Server
   Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.
   Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
   MariaDB [(none)]>
   ```

#### phpMyAdmin 连接 MariaDB

我们的部署方案中包含 phpMyAdmin 图形化工具，使用它管理 MariaDB 简单快捷：

1. 本地浏览器 Chrome 或 Firefox 访问：*http://服务器公网IP:9090*，进入phpMyAdmin
  ![登录phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-logincn-websoft9.png)

2. 输入数据库用户名和密码([不知道密码？](/zh/stack-accounts.md#mariadb))

3. 开始管理数据库
  ![phpMyadmin](https://libs.websoft9.com/Websoft9/DocsPicture/zh/mysql/phpmyadmin-adddb-websoft9.png)

> 需要了解更多 phpMyAdmin 的使用，请参考本文档 [phpMyAdmin 章节](/zh/solution-phpmyadmin.md)

## 常见问题

#### 浏览器无法访问 phpMyAdmin（白屏没有结果）？

您的服务器对应的安全组 9090 端口没有开启（入规则），导致浏览器无法它

#### phpMyAdmin 是如何安装的？

采用 Docker 安装，保证 MariaDB 环境具有良好的隔离性。