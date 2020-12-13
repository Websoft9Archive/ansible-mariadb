# FAQ

#### MariaDB 是完全免费的吗？

MariaDB Community Server   是免费开源版，MariaDB Enterprise Server 是收费开源版  

详情[对比参考](https://mariadb.com/pricing/)

#### 单台服务器上是否可以安装多个 MariaDB实例？

理论上可以，但实际上不建议

#### 什么是 MariaDB 的 Client 和 Server？

MariaDB Server 是指 MariaDB 程序本体，而 MariaDB Client 指采用TCP协议用于连接程序本地的客户端。它们是两个完全不同的程序，也就是说它们并需要同时安装到同一台服务上。


#### MariaDB 中的 test 数据库是什么？

在MariaDB5.7 版本之前，安装 MariaDB 时会默认包含一个 test 数据库，该数据库仅仅用来测试使用，但是所有能连接到MariaDB的用户，几乎都拥有test库的所有权限，因此存在一定的安全隐患。从信息安全角度考虑，如果您发现您使用的 MariaDB 中有该 test 数据库，请**务必删除**。

#### 是否可以修改 MariaDB 根目录？

可以，但不建议修改

#### 数据库 root 用户对应的密码是多少？

密码存放在服务器相关文件中：`/credentials/password.txt`

#### 是否有可视化的数据库管理工具？

有，内置phpMyAdmin

#### 如何停止 phpMyAdmin？

停止 phpMyAdmin 容器即可：

```
sudo docker stop phpmyadmin
```

#### 如何自定义 MariaDB 错误日志文件路径？

修改配置文件中下面的参数即可
```
log-error=/data/mariadb/log.err
```

#### 什么是数据库的冷备份和热备份？

冷备份就是停掉数据库服务，复制数据库文件进行备份；  
热备份就是在数据库运行中，实现不停机的备份，并保证数据库完整性。

#### 部署和安装有什么区别？

部署是将一序列软件按照不同顺序，先后安装并配置到服务器的过程，是一个复杂的系统工程。  
安装是将单一的软件拷贝到服务器之后，启动安装向导完成初始化配置的过程。  
安装相对于部署来说更简单一些。 

#### 云平台是什么意思？

云平台指提供云计算服务的平台厂家，例如：Azure,AWS,阿里云,华为云,腾讯云等

#### 实例，云服务器，虚拟机，ECS，EC2，CVM，VM有什么区别？

没有区别，只是不同厂家所采用的专业术语，实际上都是云服务器