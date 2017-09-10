### 23.6 Web 环境

SpringApplication将尝试代表您创建正确类型的ApplicationContext。 默认情况下，将使用AnnotationConfigApplicationContext或AnnotationConfigEmbeddedWebApplicationContext，具体取决于您是否正在开发Web应用程序。

用于确定“Web环境”的算法是相当简单的（基于几个类的存在）。 如果需要覆盖默认值，可以使用setWebEnvironment（boolean webEnvironment）。

也可以通过调用setApplicationContextClass() 对ApplicationContext完全控制。
    >在JUnit测试中使用SpringApplication时，通常需要调用setWebEnvironment()