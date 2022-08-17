### 一 漏洞描述
CouchDB未授权访问

Apache CouchDB是一个开源数据库,专注于易用性和成为”完全拥抱web的数据库”。它是一个使用JSON作为存储格式,JavaScript作为查询语言,MapReduce和HTTP作为API的NoSQL数据库。  

应用广泛,如BBC用在其动态内容展示平台,Credit Suisse用在其内部的商品部⻔的市场框架,Meebo,用在其社交平台(web和应用程序),默认会在5984端口开放Restful的API接口,如果使用
SSL的话就会监听在6984端口,用于数据库的管理功能。

其HTTP Server默认开启时没有进行验证,而且绑定在0.0.0.0,所有用户均可通过API访问导致未授权访问。

在官方方配置文文档中对HTTP Server的配置有WWW-Authenticate:Set this option to trigger
basic-auth popup on unauthorized requests,但是很多用户都没有这么配置,导致漏洞产生。

影响版本
小于 1.7.0 以及 小于 2.1.1

### 二 漏洞利用
未授权访问测试

curl http://192.168.0.100:5984  
curl http://192.168.0.100:5984/_config

### 三 漏洞修复
指定 CouchDB 绑定的 IP （需要重启 CouchDB 才能生效）

在 /etc/couchdb/local.ini 文件中找到 “bind_address = 0.0.0.0” ，把 0.0.0.0 修改为 127.0.0.1 ，然后保存。 

注：修改后只有本机才能访问 CouchDB。  

设置访问密码（需要重启 CouchDB 才能生效）在 /etc/couchdb/local.ini 中找到 “[admins]” 字段配置密码。  

设置 WWW-Authenticate，强制认证。



