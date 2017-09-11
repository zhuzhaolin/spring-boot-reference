### 10.1.2 Gradle 安装

Spring Boot 兼容 Gradle 2（2.9或更高版本）和Gradle 3。如果您尚未安装Gradle，您可以按照 http://www.gradle.org/ 上的说明进行操作。

可以使用org.springframework.boot 组(group)声明Spring Boot 的依赖项。 通常，您的项目将声明一个或多个“启动器(Starters)”的依赖。Spring Boot提供了一个有用的Gradle插件，可用于简化依赖关系声明和创建可执行 jar包。

Gradle Wrapper

当您需要构建项目时，Gradle Wrapper提供了一种“获取(obtaining)”Gradle的更好的方式。 它是一个小脚本和库，它与代码一起引导构建过程。 有关详细信息，请参阅 https://docs.gradle.org/2.14.1/userguide/gradle_wrapper.html 。

典型的 build.gradle 文件：
```
plugins {
    id 'org.springframework.boot' version '1.5.2.RELEASE'
    id 'java'
}
jar {
    baseName = 'myproject'
    version =  '0.0.1-SNAPSHOT'
}
repositories {
    jcenter()
}
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web")
    testCompile("org.springframework.boot:spring-boot-starter-test")
}
```