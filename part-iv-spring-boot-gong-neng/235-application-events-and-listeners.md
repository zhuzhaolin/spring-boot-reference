### 23.5 Application events and listeners

除了常见的Spring Framework事件（如 [ContextRefreshedEvent](#23-5-Application-events-and-listeners)）之外，SpringApplication还会发送一些其他应用程序事件。

    >在创建ApplicationContext之前，实际上触发了一些事件，因此您不能在@Bean上注册一个监听器。 您可以通过SpringApplication.addListeners(…) 或SpringApplicationBuilder.listeners(…)方法注册它们。

    >如果您希望自动注册这些侦听器，无论创建应用程序的方式如何，都可以将META-INF / spring.factories文件添加到项目中，并使用org.springframework.context.ApplicationListener引用您的侦听器。
org.springframework.context.ApplicationListener=com.example.project.MyListener


当您的应用程序运行时，事件按照以下顺序发送：
    1. ApplicationStartingEvent在运行开始时发送，但在注册侦听器和注册初始化器之后。
    2. 当已经知道要使用的上下文(context)环境，并在context创建之前，将发送ApplicationEnvironmentPreparedEvent。
    3. ApplicationPreparedEvent在启动刷新(refresh)之前发送，但在加载了bean定义之后。
    4.ApplicationReadyEvent在刷新之后被发送，并且处理了任何相关的回调以指示应用程序准备好服务请求。
    5. 如果启动时发生异常，则发送ApplicationFailedEvent。
    
    >一般您不需要使用应用程序事件，但可以方便地知道它们存在。 在内部，Spring Boot使用事件来处理各种任务。