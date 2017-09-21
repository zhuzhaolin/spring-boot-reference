### 27.1.8 模板引擎

除了REST Web服务，您还可以使用Spring MVC来提供动态HTML内容。 Spring MVC支持各种模板技术，包括Thymeleaf，FreeMarker和JSP。 许多其他模板引擎也运行自己的Spring MVC集成。

Spring Boot包括对以下模板引擎的自动配置支持：

    + [FreeMarker](http://freemarker.org/docs/)
    + [Groovy](http://docs.groovy-lang.org/docs/next/html/documentation/template-engines.html#_the_markuptemplateengine)
    + [Thymeleaf](http://www.thymeleaf.org/)
    + [Mustache](https://mustache.github.io/)
    
    >如果可能，应避免使用JSP，当使用嵌入式servlet容器时，JSP有几个[已知的限制](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-jsp-limitations)。
    
    
当您使用默认配置的模板引擎之一时，您的模板将从 src/main/resources/templates 自动获取。

    >IntelliJ IDEA根据运行应用程序的方式对类路径进行不同的排序。 通过main方法在IDE中运行应用程序将导致使用Maven或Gradle打包的jar运行应用程序时的不同顺序。这可能会导致Spring Boot找不到类路径上的模板。 如果您受此问题的影响，您可以重新排序IDE中的类路径，以放置模块的类和资源。 或者，您可以配置模板前缀以搜索类路径上的每个模板目录：classpath*:/templates/。
    