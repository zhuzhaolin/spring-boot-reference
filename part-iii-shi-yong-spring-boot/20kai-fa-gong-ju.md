### 20. 开发工具

Spring Boot包括一组额外的工具，可以使应用程序开发体验更加愉快。 spring-boot-devtools模块可以包含在任何项目中，以提供额外的开发时功能。 要包含devtools支持，只需将模块依赖关系添加到您的构建中：

**Maven：**
```
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
        <optional>true</optional>
    </dependency>
</dependencies>
```
**Gradle：**
```
dependencies {
    compile("org.springframework.boot:spring-boot-devtools")
}
```

    >当运行完全打包的应用程序时，开发人员工具将自动禁用。 如果您的应用程序是使用java -jar启动的，或者是使用特殊的类加载器启动，那么它将会被认为是“生产环境的应用程序”。 将开发工具依赖关系标记为可选(optional)是一种最佳做法，可以防止使用项目将devtools传递性地应用于其他模块。 Gradle不支持开箱即用的可选依赖项，因此您可能希望在此期间查看[propdeps-plugin](https://github.com/spring-projects/gradle-plugins/tree/master/propdeps-plugin)。
    
    >重新打包的jar包默认情况下不包含devtools。 如果要使用某些[远程devtools](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools-remote)功能，您需要禁用excludeDevtools 构建下的属性以包含devtools。 该属性支持Maven和Gradle插件。