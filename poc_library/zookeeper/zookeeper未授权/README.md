### 一 漏洞描述
ZooKeeper是一个分布式的，开放源码的分布式应用程序协调服务，是Google的Chubby一个开源的实现，是Hadoop和Hbase的重要组件。它是一个为分布式应用提供一致性服务的软件，提供的功能包括：配置维护、域名服务、分布式同步、组服务等。

zookeeper 未授权访问是指安装部署之后默认情况下不需要任何身份验证，从而导致 zookeeper 被远程利用，导致大量服务级别的信息泄露。

默认使用端口：2181、2182。

### 二 漏洞利用
zkCli.sh连接目标，四字命令获取敏感信息

### 三 漏洞修复
1、设置防火墙策略限制 IP 访问
2、设置用户认证和 ACL


> 参考链接  
> https://www.cnblogs.com/Hi-blog/p/Zookeeper-UnAuthorization-Access.html#_label04  
> 官方四字命令文档: https://zookeeper.apache.org/doc/r3.4.8/zookeeperAdmin.html#sc_zkCommands
