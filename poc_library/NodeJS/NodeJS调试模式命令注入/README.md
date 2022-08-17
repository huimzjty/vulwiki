### 一 漏洞描述
NodeJS Debugger - Command Injection  
该漏洞使用NodeJS V8调试器协议（version 1）的"evaluate"请求类型来评估任意JS并调用其他系统命令。    
在默认配置中，端口（默认5858）不是面向远程的，但可能会因为错误配置对外暴露。  

Node.Js 8和更高版本使用Inspector API，使用了websocket协议来进行调试。 --inspect-brk 默认监听本地端口9229  
Node.Js 7和更低版本使用Debugger API ，使用socket进行调试，--debug-brk 默认监听0.0.0.0端口5858 https://github.com/nodejs/node/pull/8106    
从Node.Js 7.7.0开始不推荐使用旧版调试器。请改用--inspect和Inspector。   
当使用版本7和更早版本中的--debug或--debug-brk开关启动时，默认情况下，Node.js在TCP 5858端口上侦听由V8调试协议定义的调试命令。任何使用此协议的调试器客户端都可以连接到正在运行的进程并对其进行调试。

### 二 漏洞利用
https://www.exploit-db.com/exploits/42793

### 三 漏洞修复
1.如无需要，关闭调试模式  
2.指定监听本地127.0.0.1  
3.升级Node.js到版本8以上  

> 参考链接  
> https://www.exploit-db.com/exploits/42793
