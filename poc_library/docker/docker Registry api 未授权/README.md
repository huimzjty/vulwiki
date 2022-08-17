### 一 漏洞描述
Docker Registry是一个无状态，高度可扩展的服务器端应用程序，可存储并允许用户使用HTTP API分发Docker映像。默认情况下Docker Registry未启用身份验证。

我们可以通过Docker Registry拉出任何容器映像并读取所有者进行的任何更改。还可以上传blob并对docker image进行更改。放置后门等。

### 二 漏洞利用
https://github.com/NotSoSecure/docker_fetch

### 三 漏洞修复
限制访问来源


> 参考链接:  
> https://saucer-man.com/information_security/437.html  
> https://notsosecure.com/anatomy-of-a-hack-docker-registry  
> https://askding.github.io/Kali/Exploit/Docker.html  
