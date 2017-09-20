### 27.3.5 JSP限制

当运行使用嵌入式servlet容器（并打包为可执行文档）的Spring Boot应用程序时，对JSP支持有一些限制。

可以使用Tomcat和war包，即可执行的war将会起作用，并且也可以部署到标准容器（不限于但包括Tomcat）中。 由于Tomcat中的硬编码文件模式，可执行的jar将无法正常工作。
可以使用Jetty和war包，即可执行的war将会起作用,并且也可以部署到任何标准的容器，它应该可以工作。
Undertow不支持JSP。
创建自定义的error.jsp页面将不会覆盖默认视图以进行[错误处理](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-error-handling)，而应使用[自定义错误页面](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-error-handling-custom-error-pages)。