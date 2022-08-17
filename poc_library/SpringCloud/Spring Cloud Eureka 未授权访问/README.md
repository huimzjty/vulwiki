### 一 漏洞描述
什么是服务治理？  
Spring Cloud封装了Netflix公司开发的Euraka模块来实现服务治理  
在传统的rpc远程调用框架中，管理每个服务与服务之间依赖关系比较复杂，管理比较复杂，所以需要使用服务治理，管理服务与服务之间依赖关系，可以实现服务调用、负载均衡、容错等，实现服务发现与注册  

什么是服务注册与发现？  
Eureka采用了CS的设计架构，Eureka Server作为服务注册功能的服务器，它是服务注册中心，而系统中的其他微服务，使用Euraka的客户端连接到Euraka Server并维持心跳连接。  
这样系统的维护人员就可以通过Euraka Server来监控系统中各个微服务是否正常运行。  
在服务注册与发现中，有一个注册中心，当服务器启动的时候，会把当前自己服务器的信息比如服务地址通讯地址等以别名方式注册到注册中心上。  
另一方（消费者|服务提供者），以该别名的方式去注册中心上获取到实际的服务通讯地址，然后再实现本地RPC调用


### 二 漏洞利用
1.普通用户可以直接访问我们的服务治理页面

2.普通用户可以将自己的服务注册到生产环景

### 三 漏洞修复
添加spring-security支持 (https://cloud.tencent.com/developer/article/1121535)

> 参考链接
> Euraka介绍: https://blog.csdn.net/weixin_46146755/article/details/123450299
> 危害以及修复: https://cloud.tencent.com/developer/article/1121535
