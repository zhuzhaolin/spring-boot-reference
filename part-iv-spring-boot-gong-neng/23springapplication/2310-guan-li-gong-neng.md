### 23.10 管理功能

可以通过指定spring.application.admin.enabled属性来为应用程序启用与管理相关的功能。 这会在平台MBeanServer上暴露SpringApplicationAdminMXBean。 您可以使用此功能来远程管理您的Spring Boot应用程序。 这对于任何服务包装器(service wrapper)实现也是有用的。

    >如果您想知道应用程序在哪个HTTP端口上运行，请使用local.server.port键获取该属性。

    >启用此功能时请小心，因为MBean公开了关闭应用程序的方法。