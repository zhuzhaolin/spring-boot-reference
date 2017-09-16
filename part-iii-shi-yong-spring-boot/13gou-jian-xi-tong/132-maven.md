### 13.2 Maven
Maven用户可以从 spring-boot-starter-parent-parent 项目中继承，以获得合理的默认值。 父项目提供以下功能：

    + Java 1.6作为默认编译器级别。
    + 源代码UTF-8编码。
    + [依赖关系管理](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-dependency-management)，允许您省略常见依赖的标签，其默认版本继承自spring-boot-dependencies POM。
    + 更合理的[资源过滤](https://maven.apache.org/plugins/maven-resources-plugin/examples/filter.html)。
    + 更合理的插件配置（[exec plugin](http://www.mojohaus.org/exec-maven-plugin/)，[surefire](https://maven.apache.org/surefire/maven-surefire-plugin/)，[Git commit ID](https://github.com/ktoso/maven-git-commit-id-plugin)，[shade](https://maven.apache.org/plugins/maven-shade-plugin/)）。
    + 针对application.properties和application.yml的更合理的资源过滤，包括特定的文件（例如application-foo.properties和application-foo.yml）
    + 最后一点：由于默认的配置文件接受Spring样式占位符（${…}），Maven过滤更改为使用 @..@ 占位符（您可以使用Maven属性resource.delimiter覆盖它）。