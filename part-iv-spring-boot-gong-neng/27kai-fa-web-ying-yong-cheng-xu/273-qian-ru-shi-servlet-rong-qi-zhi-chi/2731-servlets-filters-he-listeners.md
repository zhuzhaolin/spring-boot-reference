### 27.3.1 Servlets, Filters 和 listeners

当使用嵌入式servlet容器时，可以使用Spring bean或通过扫描Servlet组件（例如HttpSessionListener）注册Servlet规范中的Servlet，过滤器和所有监听器。

**将Servlets，过滤器和监听器注册为Spring bean**

任何Servlet，Filter或Servlet Listener 实例都会作为Spring bean注册到嵌入式容器中。 可以非常方便地在配置过程中引用您的application.properties中的值。

默认情况下，如果容器中只包含一个Servlet，它将映射到/。 在多个Servlet bean的情况下，bean名称将作为路径前缀。 过滤器(Filters)将映射到/*，默认过滤所有请求。

如果基于惯例的映射不够灵活，可以使用ServletRegistrationBean，FilterRegistrationBean和ServletListenerRegistrationBean类来完成控制。