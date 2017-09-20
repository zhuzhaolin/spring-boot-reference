### 29.3.4 在View中打开EntityManager

如果您正在运行Web应用程序，Spring Boot将默认注册[OpenEntityManagerInViewInterceptor](http://docs.spring.io/spring/docs/4.3.7.RELEASE/javadoc-api/org/springframework/orm/jpa/support/OpenEntityManagerInViewInterceptor.html)来应用“查看”中的“打开EntityManager”模式，即允许在Web视图中进行延迟加载。 如果你不想要这个行为，你应该在你的application.properties中将spring.jpa.open-in-view设置为false。