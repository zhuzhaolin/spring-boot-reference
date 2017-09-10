### 20.1 属性默认值

Spring Boots支持的几个库使用缓存来提高性能。 例如，[模板引擎](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-spring-mvc-template-engines)将缓存编译的模板，以避免重复解析模板文件。 此外，Spring MVC可以在返回静态资源时向响应中添加HTTP缓存头。

虽然缓存在生产中非常有益，但它在开发过程中可能会产生反效果，从而阻止您看到刚刚在应用程序中进行的更改。 因此，spring-boot-devtools将默认禁用这些缓存选项。

缓存选项通常由您的application.properties文件中的设置配置。 例如，Thymeleaf提供了spring.thymeleaf.cache属性。 spring-boot-devtools模块不需要手动设置这些属性，而是自动应用更加合理的开发时(development-time)配置。

    >有关应用的属性的完整列表，请参阅 [DevToolsPropertyDefaultsPostProcessor](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-devtools/src/main/java/org/springframework/boot/devtools/env/DevToolsPropertyDefaultsPostProcessor.java)。