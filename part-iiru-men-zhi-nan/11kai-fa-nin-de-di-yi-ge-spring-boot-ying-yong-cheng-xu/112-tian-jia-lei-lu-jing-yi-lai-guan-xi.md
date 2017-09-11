### 11.2 添加类路径依赖关系

Spring Boot提供了一些“启动器(Starters)”，可以方便地将jar添加到类路径中。我们的示例应用程序已经在POM的父部分使用了spring-boot-starter-parent。spring-boot-starter-parent是一个特殊启动器，提供一些Maven的默认值。它还提供依赖管理 dependency-management 标签，以便您可以省略子模块依赖关系的版本标签。

其他“启动器(Starters)”只是提供您在开发特定类型的应用程序时可能需要的依赖关系。 由于我们正在开发Web应用程序，所以我们将添加一个spring-boot-starter-web依赖关系，但在此之前，我们来看看我们目前的依赖。
```
$ mvn dependency:tree
[INFO] com.example:myproject:jar:0.0.1-SNAPSHOT
```
mvn dependency:tree：打印项目依赖关系的树形表示。 您可以看到spring-boot-starter-parent本身不在依赖关系中。 编辑pom.xml并在 parent 下添加spring-boot-starter-web依赖关系：
```
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```
如果您再次运行 mvn dependency:tree ，您将看到现在有许多附加依赖关系，包括Tomcat Web服务器和Spring Boot本身。