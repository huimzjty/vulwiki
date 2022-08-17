### 一 漏洞描述
PHP-FPM工作时，默认监听9000端口，用于接收Web服务器发送过来的FastCGI协议数据。而当我们能够通过任意方式访问到PHP-FPM的9000端口时，就可以构造数据包通过给SCRIPT_FILENAME赋值，达到执行任意PHP文件的目的

### 二 漏洞利用
https://gist.github.com/phith0n/9615e2420f31048f7e30f3937356cf75

### 三 漏洞修复
1.修改php-fpm.conf的配置：配置监听127.0.0.1

2.设置允许的客户端 为 127.0.0.1

> 参考链接  
> http://t.zoukankan.com/Gcker-p-13824041.html  
> https://www.freesion.com/article/22411393405  
> https://www.leavesongs.com/PENETRATION/fastcgi-and-php-fpm.html
