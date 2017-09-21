### 29.1.1 嵌入式数据库支持

使用内存中嵌入式数据库开发应用程序通常很方便。 显然，内存数据库不提供持久化存储; 您的应用程序启动时，您将需要初始化数据库，并在应用程序结束时丢弃数据。

    >[“How-to”部分](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-database-initialization)包含如何初始化数据库

Spring Boot可以自动配置嵌入式 [H2](http://www.h2database.com/)，[HSQL](http://hsqldb.org/) 和 [Derby](https://db.apache.org/derby/) 数据库。 您不需要提供任何连接URL，只需将要使用的嵌入式数据库的依赖关系包含进去即可。

    >如果您在测试中使用此功能，您可能会注意到，整个测试套件都会重复使用相同的数据库，而不管您使用的应用程序上下文的数量。 如果要确保每个上下文都有一个单独的嵌入式数据库，您应该将spring.datasource.generate-unique-name设置为true。
    
例如，典型的POM依赖关系是：
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.hsqldb</groupId>
    <artifactId>hsqldb</artifactId>
    <scope>runtime</scope>
</dependency>
```
    >对于要自动配置的嵌入式数据库，您需要依赖spring-jdbc。 在这个例子中，它是通过spring-boot-starter-data-jpa传递的。

    >如果由于某种原因配置嵌入式数据库的连接URL，则应注意确保数据库的自动关闭被禁用。 如果你使用H2，你应该使用DB_CLOSE_ON_EXIT=FALSE这样做。 如果您使用HSQLDB，则应确保不使用shutdown=true。 禁用数据库的自动关闭允许Spring Boot控制数据库何时关闭，从而确保在不再需要访问数据库时发生这种情况。