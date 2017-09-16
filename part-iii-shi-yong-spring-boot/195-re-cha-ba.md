### 19.5 热插拔
由于Spring Boot应用程序只是纯Java应用程序，所以JVM热插拔应该是开箱即用的。 JVM热插拔在一定程度上受到可替代的字节码的限制，更完整的解决方案，可以使用 JRebel 或者 Spring Loaded 项目。 spring-boot-devtools模块还支持快速重新启动应用程序。

有关详细信息，请参阅[第20章“开发人员工具](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools)”部分和[热插拔“操作方法](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#howto-hotswapping)”。