### 29.3 JPA 和 ‘Spring Data’

Java Persistence API是一种标准技术，可让您将对象映射到关系数据库。 spring-boot-starter-data-jpa POM提供了一种快速入门的方法。 它提供以下关键依赖：

    + Hibernate - 最受欢迎的JPA实现之一。
    + Spring Data JPA - 可以轻松实现基于JPA的存储库。
    + Spring ORMs - 来自Spring Framework的核心ORM支持。
    
    
    >我们不会在这里介绍太多的JPA或Spring Data的细节。 您可以从spring.io中查看“[使用JPA访问数据](https://spring.io/guides/gs/accessing-data-jpa/)”指南，并阅读[Spring Data JPA](http://projects.spring.io/spring-data-jpa/)和[Hibernate](http://hibernate.org/orm/documentation/)参考文档。

    >默认情况下，Spring Boot使用Hibernate 5.0.x. 但是，如果您愿意，也可以使用4.3.x或5.2.x。 请参考 [Hibernate 4](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-samples/spring-boot-sample-hibernate4) 和 [Hibernate 5.2](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-samples/spring-boot-sample-hibernate52) 示例，看看如何做到这一点。