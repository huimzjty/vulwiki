### 一 漏洞描述
Mongodb具有REST API，可以通过使用--rest开关启动MongoDB来激活它。HTTP接口的端口号比配置的MongoDB端口多1000，  
因此默认为28017。建议开发人员关闭生产服务器上的其余API和HTTP接口，因为它们允许直接访问数据库。

### 二 漏洞利用
mongo rest api 操作  
https://blog.csdn.net/i042416/article/details/124527067

### 三 漏洞修复
关闭rest api
