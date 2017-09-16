### 13.2.4 使用Spring Boot Maven插件

Spring Boot包括一个Maven插件，可以将项目打包成可执行jar。 如果要使用它，请将插件添加到部分：
```
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```
    >如果您使用Spring Boot启动器 parent pom，则只需要添加这个插件，除非您要更改parent中定义的设置，否则不需要进行配置。