### 一 漏洞描述
solr未授权访问

Search On Lucene Replication Solr是一个高性能，采用 Java 开发，基于Lucene的全文搜索服务器。  
solr未授权访问的危害很大，轻则可查询所有 数据库 信息，重则可读取系统任意文件。

### 二 漏洞利用
访问 /solr/admin
判断指纹

### 三 漏洞修复
配置solr访问控制权限
