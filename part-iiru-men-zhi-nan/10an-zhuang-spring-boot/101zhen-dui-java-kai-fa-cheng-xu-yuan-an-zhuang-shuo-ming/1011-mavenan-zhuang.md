### 10.1.1 Maven安装

Spring Boot 兼容 Apache Maven 3.2。 如果您还没有安装Maven，可以按照 https://maven.apache.org/ 上的说明进行安装。

在许多操作系统上，Maven可以通过软件包管理器进行安装。 如果您是OSX Homebrew用户，请尝试使用命令：brew install maven。 Ubuntu用户可以运行命令：sudo apt-get install maven。

Spring Boot 依赖 org.springframework.boot groupId。通常，您的Maven POM文件将从 spring-boot-starter-parent 项目继承，并声明一个或多个“启动器(启动器)”的依赖关系。Spring Boot还提供了一个可选的Maven插件来创建可执行的jar包。

典型的pom.xml文件：
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>myproject</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <!-- Inherit defaults from Spring Boot -->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.2.RELEASE</version>
    </parent>
    <!-- Add typical dependencies for a web application -->
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
    </dependencies>
    <!-- Package as an executable jar -->
    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

>    spring-boot-starter-parent是使用Spring Boot的一个很好的方式，但它并不是所有的时候都适合。有时您可能需要从不同的父POM继承，或者您可能不喜欢我们的默认设置。 [请参见第13.2.2节“使用不带父POM的Spring Boot”](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-maven-without-a-parent)作为使用导入作用域(import scope)的替代解决方案。