### 一 漏洞描述
ApacheTomcat默认安装页面中存在examples样例目录。里面存放着Servlets、JSP、WebSocket的一些服务脚本和接口等样例。其中Servletsexamples服务样例下存在一个session的样例。  
该样例可以允许用户对session来进行操控。因为session是全局通用的，利用该样例下的session来有可能操控管理员的session来进行会话传输操控管理员的账户进行恶意操作。

### 二 漏洞利用
Servletsexamples服务样例下存在一个session的样例。该样例可以允许用户对session来进行操控。  
该样例可以允许用户对session来进行操控。因为session是全局通用的，利用该样例下的session来有可能操控管理员的session来进行会话传输操控管理员的账户进行恶意操作。

### 三 漏洞修复
1、由于一般情况下，无需使用样例功能，建议您在部署完 Tomcat 后直接删除 servlets-examples 和 tomcat-docs 目录。

2、禁止访问或者直接删除examples样例目录下的资源。做目录访问权限设置，防止目录遍历。
