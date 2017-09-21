### 29.1.2 连接到生产环境数据库

生产数据库连接也可以使用连接池数据源自动配置。 这是选择具体实现的算法：

    + 我们更喜欢Tomcat连接池DataSource的性能和并发性，所以如果可用，我们总是选择它。
    + 否则，如果HikariCP可用，我们将使用它。
    + 如果Tomcat池数据源和HikariCP都不可用，并且如果Commons DBCP可用，我们将使用它，但是我们不建议在生产中使用它，并且不支持它。
    + 最后，如果Commons DBCP2可用，我们将使用它。
    
如果您使用spring-boot-starter-jdbc或spring-boot-starter-data-jpa 的startters，您将自动获得对tomcat-jdbc的依赖。

    >您可以完全绕过该算法，并通过spring.datasource.type属性指定要使用的连接池。 如果您在Tomcat容器中运行应用程序，则默认情况下提供tomcat-jdbc，这一点尤为重要。

    >可以随时手动配置其他连接池。如果您定义自己的DataSource bean，则不会发生自动配置。
    
DataSource配置由spring.datasource中的外部配置属性控制。 例如，您可以在application.properties中声明以下部分：
```
spring.datasource.url=jdbc:mysql://localhost/test
spring.datasource.username=dbuser
spring.datasource.password=dbpass
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
```

    >您应至少使用spring.datasource.url属性指定url，否则Spring Boot将尝试自动配置嵌入式数据库。

    >您通常不需要指定驱动程序类名称，因为Spring Boot可以从url为大多数数据库推断出驱动程序名称。

    >对于要创建的池数据源，我们需要能够验证有效的Driver类是否可用，所以我们在做任何事情之前检查它。 即 如果您设置spring.datasource.driver-class-name=com.mysql.jdbc.Driver，那么该类必须可加载。
    
有关更多支持的选项，请参阅 [DataSourceProperties](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/jdbc/DataSourceProperties.java)。 这些是标准选项，无论实际执行情况如何。 还可以使用各自的前缀（spring.datasource.tomcat.*，spring.datasource.hikari.*和spring.datasource.dbcp2.*）微调实现特定的设置。 有关更多详细信息，请参阅您正在使用的连接池实现的文档。

例如，如果您正在使用Tomcat连接池，您可以自定义许多其他设置：
```
# Number of ms to wait before throwing an exception if no connection is available.
spring.datasource.tomcat.max-wait=10000
# Maximum number of active connections that can be allocated from this pool at the same time.
spring.datasource.tomcat.max-active=50
# Validate the connection before borrowing it from the pool.
spring.datasource.tomcat.test-on-borrow=true
```