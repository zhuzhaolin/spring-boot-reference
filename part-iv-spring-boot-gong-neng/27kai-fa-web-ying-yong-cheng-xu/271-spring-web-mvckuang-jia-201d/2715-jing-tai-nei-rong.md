27.1.5 静态内容

默认情况下，Spring Boot将从类路径或ServletContext的根目录中的名为/static（或/ public或/resources或/META-INF/resources）的目录提供静态内容。 它使用Spring MVC中的ResourceHttpRequestHandler，因此您可以通过添加自己的WebMvcConfigurerAdapter并覆盖addResourceHandlers方法来修改该行为。

在独立的Web应用程序中，来自容器的默认servlet也被启用，并且作为后备，如果Spring决定不处理它，则从ServletContext的根目录提供内容。 大多数情况下，这不会发生（除非您修改默认的MVC配置），因为Spring将始终能够通过DispatcherServlet处理请求。

默认情况下，资源映射到/ ，但可以通过spring.mvc.static-path-pattern调整。 例如，将所有资源重定位到 /resources/可以配置如下：
```
spring.mvc.static-path-pattern=/resources/**
```

您还可以使用spring.resources.static-locations（使用目录位置列表替换默认值）来自定义静态资源位置。 如果这样做，默认欢迎页面检测将切换到您的自定义位置，因此，如果在启动时任何位置都有一个index.html，它将是应用程序的主页。

除了上述“标准”静态资源位置之外，还提供了一个特殊情况，用于[Webjars内容](http://www.webjars.org/)。 任何具有/ webjars / **中路径的资源都将从jar文件中提供，如果它们以Webjars格式打包。

如果您的应用程序将被打包为jar，请不要使用 src/main/webapp 目录。 虽然这个目录是一个通用的标准，但它只适用于war包，如果生成一个jar，它将被大多数构建工具忽略。

Spring Boot还支持Spring MVC提供的高级资源处理功能，允许使用例如缓存静态资源或使用Webjars的版本无关的URL。

要为Webjars使用版本无关的URL，只需添加webjars-locator依赖关系即可。然后声明您的Webjar，以jQuery为例，如“/webjars/jquery/dist/jquery.min.js”，这将产生“/webjars/jquery/xyz/dist/jquery.min.js”，其中xyz是Webjar版本 。

    >如果您使用JBoss，则需要声明webjars-locator-jboss-vfs依赖关系而不是webjars-locator; 否则所有Webjars都将解析为404。
    
要使用缓存清除功能，以下配置将为所有静态资源配置缓存清除解决方案，从而有效地在URL中添加内容哈希值，例如：
```
spring.resources.chain.strategy.content.enabled=true
spring.resources.chain.strategy.content.paths=/**
```
    >链接资源在运行时在模板中被重写，这归功于自动配置为Thymeleaf和FreeMarker的ResourceUrlEncodingFilter。 使用JSP时，应手动声明此过滤器。 其他模板引擎现在不会自动支持，但可以使用自定义模板宏/帮助程序和使用[ResourceUrlProvider](http://docs.spring.io/spring/docs/4.3.7.RELEASE/javadoc-api/org/springframework/web/servlet/resource/ResourceUrlProvider.html)。
    
当使用例如JavaScript模块加载器动态加载资源时，重命名文件不是一个选项。这就是为什么其他策略也得到支持并可以合并的原因。 “固定(fixed)”策略将在URL中添加静态版本字符串，而不更改文件名：
```
spring.resources.chain.strategy.content.enabled=true
spring.resources.chain.strategy.content.paths=/**
spring.resources.chain.strategy.fixed.enabled=true
spring.resources.chain.strategy.fixed.paths=/js/lib/
spring.resources.chain.strategy.fixed.version=v12
``` 
使用此配置，位于“/js/lib/”下的JavaScript模块将使用固定版本策略“/v12/js/lib/mymodule.js”，而其他资源仍将使用内容。 

有关更多支持的选项，请参阅[ResourceProperties](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/web/ResourceProperties.java)。 

    >此功能已在专门的[博客文章](https://spring.io/blog/2014/07/24/spring-framework-4-1-handling-static-web-resources)和Spring Framework[参考文档](http://docs.spring.io/spring/docs/4.3.7.RELEASE/spring-framework-reference/htmlsingle/#mvc-config-static-resources)中进行了详细描述。