### 一 漏洞描述
XDebug是PHP的一个扩展，用于调试PHP代码。如果目标开启了远程调试模式，并设置remote_connect_back = 1：
```
xdebug.remote_connect_back = 1
xdebug.remote_enable = 1
```
这个配置下，我们访问http://target/index.php?XDEBUG_SESSION_START=phpstorm，目标服务器的XDebug将会连接访问者的IP（或X-Forwarded-For头指定的地址）并通过dbgp协议与其通信，我们通过dbgp中提供的eval方法即可在目标服务器上执行任意PHP代码。

### 二 漏洞利用
监听端口，通过x-forwarded-for让服务器回连端口，通过dbgp发送执行代码

### 三 漏洞修复
1.不要使用remote_connect_back，使用xdebug.remote_host指定具体的ip。

2.修改xdebug.idekey为随机字符。

3.调试模式用完之后，立马取消调试模式。

> 参考链接  
> https://blog.csdn.net/zy15667076526/article/details/111824491
