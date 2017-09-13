### 13.5 启动器

启动器是一组方便的依赖关系描述符，可以包含在应用程序中。 您可以获得所需的所有Spring和相关技术的一站式服务，无需通过示例代码搜索和复制粘贴依赖配置。 例如，如果要开始使用Spring和JPA进行数据库访问，那么只需在项目中包含spring-boot-starter-data-jpa依赖关系即可。

启动器包含许多依赖关系，包括您需要使项目快速启动并运行，并具有一致的受支持的依赖传递关系。

**What’s in a name**

所有正式起动器都遵循类似的命名模式： spring-boot-starter- ，其中 是特定类型的应用程序。 这个命名结构旨在帮助你快速找到一个启动器。 许多IDE中的Maven插件允许您按名称搜索依赖项。 例如，安装Eclipse或STS的Maven插件后，您可以简单地在POM编辑器中点击 Dependency Hierarchy，并在filter输入“spring-boot-starter”来获取完整的列表。  
如创建自己的启动器部分所述，第三方启动程序不应该从Spring-boot开始，因为它是为正式的Spring Boot artifacts 保留的。 acme 的 第三方启动器通常被命名为acme-spring-boot-starter。

Spring Boot在org.springframework.boot组下提供了以下应用程序启动器：

表13.1. Spring Boot应用程序启动器

| 名称 | 描述 | Pom |
| :---: | :---: | :---: |
| spring-boot-starter-thymeleaf | 使用Thymeleaf视图构建MVC Web应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-thymeleaf/pom.xml) |
| spring-boot-starter-data-couchbase | 使用Couchbase面向文档的数据库和Spring Data Couchbase的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-couchbase/pom.xml) |
| spring-boot-starter-artemis | 使用Apache Artemis的JMS启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-artemis/pom.xml) |
| spring-boot-starter-artemis | Spring Web Services 启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-web-services/pom.xm) |
| spring-boot-starter-mail | Java Mail和Spring Framework的电子邮件发送支持的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-web-services/pom.xm) |
| spring-boot-starter-data-redis | Redis key-value 数据存储与Spring Data Redis和Jedis客户端启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-redis/pom.xml) |
| spring-boot-starter-web | 使用Spring MVC构建Web，包括RESTful应用程序。使用Tomcat作为默认的嵌入式容器的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-web/pom.xml) |
| spring-boot-starter-data-gemfire | 使用GemFire分布式数据存储和Spring Data GemFire的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-web/pom.xml) |
| spring-boot-starter-activemq | 使用Apache ActiveMQ的JMS启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-activemq/pom.xml) |
| spring-boot-starter-data-elasticsearch | 使用Elasticsearch搜索和分析引擎和Spring Data Elasticsearch的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-elasticsearch/pom.xml) |
| spring-boot-starter-integration | Spring Integration 启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-integration/pom.xml) |
| spring-boot-starter-test | 使用JUnit，Hamcrest和Mockito的库测试Spring Boot应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-test/pom.xml) |
| spring-boot-starter-jdbc | 使用JDBC与Tomcat JDBC连接池的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jdbc/pom.xml) |
| spring-boot-starter-mobile | 使用JDBC与Tomcat JDBC连接池的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-mobile/pom.xml) |
| spring-boot-starter-validation | 使用Java Bean Validation 与Hibernate Validator的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-validation/pom.xml) |
| spring-boot-starter-hateoas | 使用Spring MVC和Spring HATEOAS构建基于超媒体的RESTful Web应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-hateoas/pom.xml) |
| spring-boot-starter-jersey | 使用JAX-RS和Jersey构建RESTful Web应用程序的启动器。spring-boot-starter-web的替代方案 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jersey/pom.xml) |
| spring-boot-starter-data-neo4j | 使用Neo4j图数据库和Spring Data Neo4j的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-neo4j/pom.xml) |
| pring-boot-starter-data-ldap | 使用Spring Data LDAP的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-ldap/pom.xml) |
| spring-boot-starter-websocket | 使用Spring Framework的WebSocket支持构建WebSocket应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-websocket/pom.xml) |
| spring-boot-starter-aop | 使用Spring AOP和AspectJ进行面向切面编程的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-websocket/pom.xml) |
| spring-boot-starter-amqp | 使用Spring AMQP和Rabbit MQ的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-websocket/pom.xml) |
| spring-boot-starter-data-cassandra | 使用Cassandra分布式数据库和Spring Data Cassandra的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-cassandra/pom.xml) |
| spring-boot-starter-social-facebook | 使用Spring Social Facebook 的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-social-facebook/pom.xml) |
| spring-boot-starter-jta-atomikos | 使用Atomikos的JTA事务的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jta-atomikos/pom.xml) |
| spring-boot-starter-security | 使用Spring Security的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-security/pom.xml) |
| spring-boot-starter-mustache | 使用Mustache视图构建MVC Web应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-mustache/pom.xml) |
| spring-boot-starter-data-jpa | 使用Spring数据JPA与Hibernate的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-jpa/pom.xml) |
| spring-boot-starter | 核心启动器，包括自动配置支持，日志记录和YAML | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter/pom.xml) |
| spring-boot-starter-groovy-templates | 使用Groovy模板视图构建MVC Web应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-groovy-templates/pom.xml) |
| spring-boot-starter-freemarker | 使用FreeMarker视图构建MVC Web应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-groovy-templates/pom.xml) |
| spring-boot-starter-batch | 使用Spring Batch的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-batch/pom.xml) |
| spring-boot-starter-social-linkedin | 使使用Spring Social LinkedIn的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-social-linkedin/pom.xml) |
| spring-boot-starter-cache | 使用Spring Framework缓存支持的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-cache/pom.xml) |
| spring-boot-starter-data-solr | 使用Apache Solr搜索平台与Spring Data Solr的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-solr/pom.xml) |
| spring-boot-starter-data-mongodb | 使用MongoDB面向文档的数据库和Spring Data MongoDB的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-mongodb/pom.xml) |
| spring-boot-starter-jooq | 使用jOOQ访问SQL数据库的启动器。 spring-boot-starter-data-jpa或spring-boot-starter-jdbc的替代方案 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jooq/pom.xml) |
| spring-boot-starter-cloud-connectors | 使用Spring Cloud连接器，简化了与Cloud Foundry和Heroku等云平台中的服务连接的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-cloud-connectors/pom.xml) |
| spring-boot-starter-jta-narayana | Spring Boot Narayana JTA 启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jta-bitronix/pom.xml) |
| spring-boot-starter-jta-bitronix | 使用Spring Cloud连接器，简化了与Cloud Foundry和Heroku等云平台中的服务连接的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jta-bitronix/pom.xml) |
| spring-boot-starter-social-twitter | 使用Spring Social Twitter的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-social-twitter/pom.xml) |
| spring-boot-starter-data-rest | 通过使用Spring Data REST在REST上暴露Spring数据库的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-data-rest/pom.xml) |

除了应用程序启动器，以下启动器可用于添加[生产准备\(production ready\)](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#production-ready)功能：

**表13.2 Spring Boot生产环境启动器**

| 名称 | 描述 | Pom |
| :---: | :---: | :---: |
| spring-boot-starter-actuator | 使用Spring Boot Actuator提供生产准备功能，可帮助您监控和管理应用程序的启动器 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-actuator/pom.xml) |
| spring-boot-starter-remote-shell | 使用CRaSH远程shell通过SSH监视和管理您的应用程序的启动器。 自1.5以来已弃用 | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-remote-shell/pom.xml) |

最后，Spring Boot还包括一些启动器，如果要排除或替换特定的技术，可以使用它们：

|  名称  |  描述  |  Pom |
| :--- | :--- |:----|
| spring-boot-starter-undertow   |  使用Undertow作为嵌入式servlet容器的启动器。 spring-boot-starter-tomcat的替代方案  |  [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-undertow/pom.xml) |
| spring-boot-starter-jetty |  使用Jetty作为嵌入式servlet容器的启动器。 spring-boot-starter-tomcat的替代方案  | [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-jetty/pom.xml)  |
| spring-boot-starter-logging  | 使用Logback进行日志记录的启动器。 默认的日志启动器   | [Pom ](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-logging/pom.xml) |
| spring-boot-starter-tomcat  |  使用Tomcat作为嵌入式servlet容器的启动器。 spring-boot-starter-web的默认servlet容器启动器  |  [Pom](http://note.youdao.com/) |
| spring-boot-starter-log4j2  |  使用Log4j2进行日志记录的启动器。 spring-boot-start-logging的替代方法  |  [Pom](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-starters/spring-boot-starter-log4j2/pom.xml) |


