### 27.2 JAX-RS 和 Jersey

如果您喜欢JAX-RS编程模型的REST endpoints ，您可以使用一个可用的实现而不是Spring MVC。 如果您刚刚在应用程序上下文中注册了一个@Bean的Servlet或Filter，那么Jersey 1.x和Apache CXF的功能非常出色。 Jersey2.x有一些本地Spring支持，所以我们也提供自动配置支持它在Spring Boot与启动器。

要开始使用Jersey 2.x，只需将spring-boot-starter-jersey作为依赖项，然后您需要一个@Bean类型ResourceConfig，您可以在其中注册所有端点(endpoints)：

```
@Component
public class JerseyConfig extends ResourceConfig {
    public JerseyConfig() {
        register(Endpoint.class);
    }
}
```

    >Jersey对扫描可执行档案的包是相当有限的。 例如，当运行可执行的war文件时，它无法扫描在WEB-INF/classes中找到的包中的端点(endpoints)。 为了避免这种限制，不应使packages方法，并且应使用上述寄存器方法单独注册(register)端点。
    
您还可以注册任意数量的ResourceConfigCustomizer的实现bean，以实现更高级的自定义。

所有注册的端点都应为具有HTTP资源注解（@GET等）的@Components，例如。

```
@Component
@Path("/hello")
public class Endpoint {
    @GET
    public String message() {
        return "Hello";
    }
}
```

由于Endpoint是一个Spring @Component，所以Spring的生命周期由Spring管理，您可以使用@Autowired依赖关系并使用@Value注入外部配置。 默认情况下，Jersey servlet将被注册并映射到/ *。 您可以通过将@ApplicationPath添加到ResourceConfig来更改映射。

默认情况下，Jersey将通过@Bean以名为jerseyServletRegistration的ServletRegistrationBean类型在Servlet进行设置。 默认情况下，servlet将被初始化，但是您可以使用spring.jersey.servlet.load-on-startup进行自定义。您可以通过创建一个自己的同名文件来禁用或覆盖该bean。 您也可以通过设置spring.jersey.type = filter（在这种情况下，@Bean来替换或替换为jerseyFilterRegistration），使用Filter而不是Servlet。 servlet有一个@Order，您可以使用spring.jersey.filter.order设置。 可以使用spring.jersey.init.* 给出Servlet和过滤器注册的init参数，以指定属性的映射。

有一个[Jersey示例](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-samples/spring-boot-sample-jersey)，所以你可以看到如何设置。 还有一个[Jersey1.x示例](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-samples/spring-boot-sample-jersey1)。 请注意，在Jersey1.x示例中，spring-boot maven插件已经被配置为打开一些Jersey jar，以便它们可以被JAX-RS实现扫描（因为示例要求它们在Filter注册中进行扫描） 。 如果您的任何JAX-RS资源作为嵌套的jar打包，您可能需要执行相同操作。