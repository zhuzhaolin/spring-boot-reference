### 24.3 应用程序属性文件

SpringApplication将从以下位置的application.properties文件中加载属性，并将它们添加到Spring Environment中：

1. 当前目录的/config子目录
2. 当前目录  
3. classpath中/config包  
4. classpath root路径

该列表按优先级从高到低排序。

    >也可以[使用YAML（’.yml’）文件](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#boot-features-external-config-yaml)替代“.properties”。
    
如果您不喜欢application.properties作为配置文件名，可以通过指定一个spring.config.name Spring environment属性来切换到另一个。 您还可以使用spring.config.location环境属性（用逗号分隔的目录位置列表或文件路径）显式引用位置。

```
$ java -jar myproject.jar --spring.config.name=myproject
```
或
```
$ java -jar myproject.jar --spring.config.location=classpath:/default.properties,classpath:/override.properties
```
    >spring.config.name和spring.config.location一开始就被用于确定哪些文件必须被加载，因此必须将它们定义为环境属性（通常是OS env，system属性或命令行参数）。
    
如果spring.config.location包含的如果是目录而非文件，那么它们应该以/结尾（并将在加载之前附加从spring.config.name生成的名称，包括profile-specific的文件名）。 在spring.config.location中指定的文件按原样使用，不支持特定于配置文件的变体，并且将被任何特定于配置文件的属性覆盖。 

   默认的搜索路径 classpath:,classpath:/config,file:,file:config/ 始终会被搜索，不管spring.config.location的值如何。 该搜索路径从优先级排序从低到高（file:config/最高）。 如果您指定自己的位置，则它们优先于所有默认位置，并使用相同的从最低到最高优先级排序。 这样，您可以在application.properties（或使用spring.config.name选择的任何其他基础名称）中为应用程序设置默认值，并在运行时使用不同的文件覆盖它，并保留默认值。
   
   >如果您使用环境(environment)变量而不是系统属性，大多数操作系统不允许使用句点分隔(period-separated)的键名称，但可以使用下划线（例如，SPRING_CONFIG_NAME，而不是spring.config.name）

   >如果您运行在容器中，则可以使用JNDI属性（在 java:comp/env 中）或servlet上下文初始化参数，而不是环境变量或系统属性。
   
      
            