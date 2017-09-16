### 13.1 依赖管理

每个版本的Spring Boot提供了一个它所支持的依赖关系列表。 实际上，您不需要为构建配置文件中的这些依赖关系提供版本，因为Spring Boot会为您进行管理这些依赖的版本。 当您升级Spring Boot本身时，这些依赖关系也将以一致的进行升级。

    >如果您觉得有必要，您仍然可以指定一个版本并覆盖Spring Boot建议的版本。
    
   管理的列表中包含可以使用Spring Boot的所有Spring模块以及第三方库的精简列表。 该列表可作为标准的[物料(Materials)清单（spring-boot-dependencies）](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-maven-without-a-parent)使用，并且还提供了对 [Maven](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-maven-parent-pom) 和 [Gradle](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#build-tool-plugins-gradle-dependency-management) 的额外支持。
       >Spring Boot的每个版本与Spring Framework的基本版本相关联，因此我们强烈建议您不要自己指定其版本。