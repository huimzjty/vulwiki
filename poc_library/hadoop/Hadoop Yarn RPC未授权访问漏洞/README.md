### 一 漏洞描述
Apache Hadoop YARN （Yet Another Resource Negotiator）是一种新的 Hadoop  资源管理器，它是一个通用资源管理系统，可为上层应用提供统一的资源管理和调度，它的引入为集群在利用率、资源统一管理和数据共享等方面带来了巨大好处。  

Hadoop Yarn默认对外开放RPC服务，攻击者可利用RPC服务执行任意命令，进而控制服务器。同时由于Hadoop Yarn  RPC服务访问控制机制开启方式与REST API不一样，因此即使在 REST API有授权认证的情况下，RPC服务所在端口仍然可以未授权访问。

### 二 漏洞利用
https://github.com/cckuailong/YarnRpcRCE

`java -jar YarnRpcUnauth.jar {ip}:{port} "{command}"`

### 三 漏洞修复
(临时修复建议)
1. Apache Hadoop官方建议用户开启Kerberos认证。
2. 设置 Hadoop RPC服务所在端口仅对可信地址开放。
3. 建议升级并启用Kerberos的认证功能，阻止未经授权的访问。


> 参考链接  
> https://developer.aliyun.com/article/824738
