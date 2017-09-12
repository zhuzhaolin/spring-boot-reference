### 13.3 Gradle

Gradle用户可以直接在其依赖关系部分导入“启动器”。 不像Maven，没有“超级父”导入来共享一些配置。
```
repositories {
    jcenter()
}
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web:1.5.2.RELEASE")
}
```
spring-boot-gradle-plugin也是可用的，它提供了从源代码创建可执行jar并运行项目的任务。 它还提供依赖关系管理，除其他功能外，还允许您省略由Spring Boot管理的任何依赖关系的版本号：
```
plugins {
    id 'org.springframework.boot' version '1.5.2.RELEASE'
    id 'java'
}
repositories {
    jcenter()
}
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web")
    testCompile("org.springframework.boot:spring-boot-starter-test")
}
```