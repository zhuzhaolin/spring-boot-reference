### 27.3.4 定制嵌入式servlet容器

可以使用Spring Environment属性配置常见的servlet容器设置。 通常您可以在application.properties文件中定义属性。

常用服务器设置包括：

    + 网络设置：侦听端口的HTTP请求（server.port），接口地址绑定到server.address等。
    + 会话设置：会话是否持久化（server.session.persistence），会话超时（server.session.timeout），会话数据的位置（server.session.store-dir）和session-cookie配置（server.session.cookie.*）。
    + 错误管理：错误页面的位置（server.error.path）等
    + [SSL](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-configure-ssl)
    + [HTTP压缩](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#how-to-enable-http-response-compression)
    
Spring Boot尽可能地尝试公开常见设置，但并不总是可能的。 对于这些情况，专用命名空间提供服务器特定的定制（请参阅server.tomcat和server.undertow）。 例如，可以使用嵌入式servlet容器的特定功能来配置[访问日志](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-configure-accesslogs)。

    >有关完整列表，请参阅 [ServerProperties](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/web/ServerProperties.java) 类。
    
**用程序定制**

如果需要以编程方式配置嵌入式servlet容器，您可以注册一个实现EmbeddedServletContainerCustomizer接口的Spring bean。 EmbeddedServletContainerCustomizer提供对ConfigurableEmbeddedServletContainer的访问，其中包含许多自定义设置方法。
```
import org.springframework.boot.context.embedded.*;
import org.springframework.stereotype.Component;
@Component
public class CustomizationBean implements EmbeddedServletContainerCustomizer {
    @Override
    public void customize(ConfigurableEmbeddedServletContainer container) {
        container.setPort(9000);
    }
}
```
**直接自定义ConfigurableEmbeddedServletContainer**

如果上述定制技术有太多限制，您可以自己注册TomcatEmbeddedServletContainerFactory，JettyEmbeddedServletContainerFactory或UndertowEmbeddedServletContainerFactory bean。
```
@Bean
public EmbeddedServletContainerFactory servletContainer() {
    TomcatEmbeddedServletContainerFactory factory = new TomcatEmbeddedServletContainerFactory();
    factory.setPort(9000);
    factory.setSessionTimeout(10, TimeUnit.MINUTES);
    factory.addErrorPages(new ErrorPage(HttpStatus.NOT_FOUND, "/notfound.html"));
    return factory;
}
```
setter方法提供了许多配置选项。 如果您需要做更多的自定义，还会提供几种保护方法“钩子”。 有关详细信息，请参阅源代码文档。