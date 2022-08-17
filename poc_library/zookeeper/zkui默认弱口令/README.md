### 一 漏洞描述
简介zkui它提供了一个管理界面，可以针对zookeepr的节点值进行CRUD操作，同时也提供了安全认证。    
其默认口令为 {"admin":"manager"}。 

### 二 漏洞利用
尝试登录，但只能做节点crud操作

### 三 漏洞修复
修改口令

> 参考链接  
> https://blog.csdn.net/HeatDeath/article/details/79045059
