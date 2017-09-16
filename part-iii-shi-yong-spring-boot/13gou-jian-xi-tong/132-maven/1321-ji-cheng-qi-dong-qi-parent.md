### 13.2.1 继承启动器parent

要将项目配置为继承spring-boot-starter-parent，只需设置标签如下：
```
<!-- Inherit defaults from Spring Boot -->
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.2.RELEASE</version>
</parent>
```
    > 您只需要在此依赖项上指定Spring Boot版本号。 如果您导入其他起始器，则可以放心地省略他们的版本号。
    
 通过该设置，您还可以通过覆盖自己的项目中的属性来覆盖单个依赖。 例如，要升级到另一个 Spring Data 版本序列，您需要将以下内容添加到您的pom.xml中。
 ```
 <properties>
    <spring-data-releasetrain.version>Fowler-SR2</spring-data-releasetrain.version>
</properties>   
```
    > 检查 [spring-boot-dependencies pom ](https://github.com/spring-projects/spring-boot/tree/v1.5.2.RELEASE/spring-boot-dependencies/pom.xml)以获取支持的属性列表。