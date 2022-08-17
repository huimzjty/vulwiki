### 一 漏洞描述
PHP 8.1.0-dev 版本在2021年3月28日被植入后门，但是后门很快被发现并清除。当服务器存在该后门时，攻击者可以通过发送User-Agentt头来执行任意代码。

### 二 漏洞利用
`User-Agentt: zerodiumsystem('id');`

### 三 漏洞修复
升级

> 参考链接  
> https://blog.csdn.net/qq_44159028/article/details/116992989
