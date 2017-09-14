### 16. 自动配置

Spring Boot 会根据您添加的jar依赖关系自动配置您的Spring应用程序。例如，如果HSQLDB在您的类路径上，并且您没有手动配置任何数据库连接bean，那么我们将自动配置内存数据库。

您需要通过将@EnableAutoConfiguration或@SpringBootApplication注解添加到您的一个@Configuration类中来选择自动配置。

    >您应该只添加一个@EnableAutoConfiguration注解。 我们通常建议您将其添加到主@Configuration类中。