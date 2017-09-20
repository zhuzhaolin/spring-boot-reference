### 29.1.3 连接到JNDI DataSource

如果要将Spring Boot应用程序部署到应用程序服务器，则可能需要使用应用程序服务器内置功能来配置和管理DataSource，并使用JNDI进行访问。

spring.datasource.jndi-name属性可以用作spring.datasource.url，spring.datasource.username和spring.datasource.password属性的替代方法，以从特定的JNDI位置访问DataSource。 例如，application.properties中的以下部分显示了如何访问JBoss AS定义的DataSource：

```
spring.datasource.jndi-name=java:jboss/datasources/customers
```