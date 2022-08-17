### 一 漏洞描述
Actuator 是 Spring Boot 提供的服务监控和管理中间件，默认配置会导致接口未授权访问，部分接口会泄露网站配置信息、流量信息和内存信息等，如果工程还使用了 Jolokia 依赖，攻击者甚至可以远程执行任意代码，获取服务器权限。

### 二 漏洞利用
利用1  
通过“/jolokia”远程执行代码  
https://github.com/mpgn/Spring-Boot-Actuator-Exploit

利用2  
XStream反序列化

利用3  
spring.cloud.bootstrap.location 命令执行

利用4  
/trace 路径获取用户认证字段信息

利用5
env信息泄露，加密属性值获取方式
1 找到属性名: GET 请求目标网站的 /env 或 /actuator/env 接口，搜索 ****** 关键词
2 获取jvm heap：请求目标的 /heapdump 或 /actuator/heapdump 接口，下载应用的JVM 堆信息
3 使用 MAT工具查看

利用6
/health 可能存在项目git地址物理地址


### 三 漏洞修复
使用安全依赖

> 参考链接
> https://www.veracode.com/blog/research/exploiting-spring-boot-actuators
> https://www.jianshu.com/p/c2206b8154ad
> https://r0yanx.com/2020/06/05/Spring-Boot-Actuators%E6%9C%AA%E6%8E%88%E6%9D%83GetShell/
> https://www.freebuf.com/news/193509.html
