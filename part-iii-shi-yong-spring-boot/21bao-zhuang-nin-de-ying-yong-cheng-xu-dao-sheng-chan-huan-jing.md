### 21. 包装您的应用程序到生产环境

可执行的jar可用于生产部署。 由于它们是相互独立的，它们也非常适合基于云的部署。

对于其他“生产环境准备”功能，如健康，审计和metric REST或JMX端点; 考虑添加spring-boot-actuator。 有关详细信息，请参见[第V部分“Spring Boot Actuator：生产环境准备功能](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#production-ready)”。