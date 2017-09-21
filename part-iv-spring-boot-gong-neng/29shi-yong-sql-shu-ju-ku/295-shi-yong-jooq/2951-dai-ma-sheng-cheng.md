### 29.5.1 代码生成

为了使用jOOQ类型安全的查询，您需要从数据库模式生成Java类。 您可以按照j[OOQ用户手册](http://www.jooq.org/doc/3.6/manual-single-page/#jooq-in-7-steps-step3)中的说明进行操作。 如果您正在使用jooq-codegen-maven插件（并且还使用spring-boot-starter-parent“父POM”），您可以安全地省略插件的标签。 您还可以使用Spring Boot定义的版本变量（例如h2.version）来声明插件的数据库依赖关系。 以下是一个例子：

```
<plugin>
    <groupId>org.jooq</groupId>
    <artifactId>jooq-codegen-maven</artifactId>
    <executions>
        ...
    </executions>
    <dependencies>
        <dependency>
            <groupId>com.h2database</groupId>
            <artifactId>h2</artifactId>
            <version>${h2.version}</version>
        </dependency>
    </dependencies>
    <configuration>
        <jdbc>
            <driver>org.h2.Driver</driver>
            <url>jdbc:h2:~/yourdatabase</url>
        </jdbc>
        <generator>
            ...
        </generator>
    </configuration>
</plugin>
```