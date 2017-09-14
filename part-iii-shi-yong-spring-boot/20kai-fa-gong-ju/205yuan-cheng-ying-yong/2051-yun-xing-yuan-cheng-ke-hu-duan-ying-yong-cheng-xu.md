### 20.5.1 运行远程客户端应用程序
远程客户端应用程序旨在从IDE中运行。 您需要使用与要连接的远程项目相同的类路径运行org.springframework.boot.devtools.RemoteSpringApplication。 传递给应用程序的必选参数应该是您要连接到的远程URL。

例如，如果您使用Eclipse或STS，并且有一个名为my-app的项目已部署到Cloud Foundry，则可以执行以下操作：

从Run 菜单中选择Run Configurations…。
创建一个新的Java Application “launch configuration”。
浏览my-app项目。
使用org.springframework.boot.devtools.RemoteSpringApplication作为主类。
将https://myapp.cfapps.io添加到程序参数（或任何远程URL）中。

运行的远程客户端将如下所示：

```
 .   ____          _                                              __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _          ___               _      \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` |        | _ \___ _ __  ___| |_ ___ \ \ \ \
 \\/  ___)| |_)| | | | | || (_| []::::::[]   / -_) '  \/ _ \  _/ -_) ) ) ) )
  '  |____| .__|_| |_|_| |_\__, |        |_|_\___|_|_|_\___/\__\___|/ / / /
 =========|_|==============|___/===================================/_/_/_/
 :: Spring Boot Remote :: 1.5.2.RELEASE
2015-06-10 18:25:06.632  INFO 14938 --- [           main] o.s.b.devtools.RemoteSpringApplication   : Starting RemoteSpringApplication on pwmbp with PID 14938 (/Users/pwebb/projects/spring-boot/code/spring-boot-devtools/target/classes started by pwebb in /Users/pwebb/projects/spring-boot/code/spring-boot-samples/spring-boot-sample-devtools)
2015-06-10 18:25:06.671  INFO 14938 --- [           main] s.c.a.AnnotationConfigApplicationContext : Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@2a17b7b6: startup date [Wed Jun 10 18:25:06 PDT 2015]; root of context hierarchy
2015-06-10 18:25:07.043  WARN 14938 --- [           main] o.s.b.d.r.c.RemoteClientConfiguration    : The connection to http://localhost:8080 is insecure. You should use a URL starting with 'https://'.
2015-06-10 18:25:07.074  INFO 14938 --- [           main] o.s.b.d.a.OptionalLiveReloadServer       : LiveReload server is running on port 35729
2015-06-10 18:25:07.130  INFO 14938 --- [           main] o.s.b.devtools.RemoteSpringApplication   : Started RemoteSpringApplication in 0.74 seconds (JVM running for 1.105)
```

 >由于远程客户端正在使用与实际应用程序相同的类路径，因此可以直接读取应用程序属性。 这是spring.devtools.remote.secret属性如何读取并传递到服务器进行身份验证。

>建议使用https//作为连接协议，以便流量被加密，防止密码被拦截。

>如果需要使用代理访问远程应用程序，请配置spring.devtools.remote.proxy.host和spring.devtools.remote.proxy.port属性。