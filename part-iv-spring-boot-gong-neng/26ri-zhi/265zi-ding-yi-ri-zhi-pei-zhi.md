### 26.5 自定义日志配置

可以通过在类路径中包含适当的库来激活各种日志系统，并通过在类路径的根目录中提供合适的配置文件，或在Spring Environment属性logging.config指定的位置进一步配置。

您可以使用org.springframework.boot.logging.LoggingSystem系统属性强制Spring Boot使用特定的日志记录系统。该值应该是LoggingSystem实现的全名。 您还可以使用none值完全禁用Spring Boot的日志记录配置。

> 由于在创建ApplicationContext之前初始化日志，因此无法在Spring @Configuration文件中控制@PropertySources的日志记录。 系统属性和常规的Spring Boot外部配置文件工作正常。

根据您的日志记录系统，将会加载以下文件：

| Logging System | Customization |
| :--- | :--- |
| Logback | logback-spring.xml, logback-spring.groovy, logback.xml or logback.groovy |
| Log4j2 | log4j2-spring.xml or log4j2.xml |
| JDK \(Java Util Logging\) | logging.properties |

> 如果可能，我们建议您使用-spring变体进行日志记录配置（例如使用logback-spring.xml而不是logback.xml）。 如果使用标准配置位置，则Spring无法完全控制日志初始化。
>
> Java Util Logging存在已知的类加载问题，从“可执行jar”运行时会导致问题。 我们建议您尽可能避免

帮助定制一些其他属性从Spring环境转移到系统属性：

| Spring Environment | System Property | Comments |
| :--- | :--- | :--- |
| logging.exception-conversion-word | LOG_EXCEPTION_CONVERSION_WORD | 记录异常时使用的转换字 |
| logging.file | LOG_FILE | 如果定义了，则用于默认日志配置。 |
| logging.path | LOG_PATH | 如果定义了，则用于默认日志配置。 |
| logging.pattern.console | CONSOLE_LOG_PATTERN | 	在控制台上使用的日志模式（stdout）。 （仅支持默认logback设置。） |
| logging.pattern.file | FILE_LOG_PATTERN |  在文件中使用的日志模式（如果LOG_FILE已启用）。 （仅支持默认logback设置。）|
| logging.pattern.level | LOG_LEVEL_PATTERN | 用于呈现日志级别的格式（默认％5p）。 （仅支持默认logback设置。） |
| PID | PID | 当前进程ID（如果可能的话，当未被定义为OS环境变量时被发现） |

支持的所有日志记录系统在分析其配置文件时可以查看系统属性。 有关示例，请参阅spring-boot.jar中的默认配置。

    >如果要在logging属性中使用占位符，则应使用Spring Boot的语法，而不是底层框架的语法。 值得注意的是，如果您使用Logback，您应该使用：作为属性名称与其默认值之间的分隔符，而不是:-。

    >您可以通过覆盖LOG_LEVEL_PATTERN（或Logback的log.pattern.level）来添加MDC和其他ad-hoc内容到日志行。 例如，如果使用logging.pattern.level = user：％X {user}％5p，则默认日志格式将包含“user”的MDC条目（如果存在）。

```
2015-09-30 12:30:04.031 user:juergen INFO 22174 --- [  nio-8080-exec-0] demo.Controller
Handling authenticated request
```




