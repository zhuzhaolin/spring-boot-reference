### 13.2.2 使用没有父POM的 Spring Boot

不是每个人都喜欢从spring-boot-starter-parent POM继承。 您公司可能有自己标准的父母，或者您可能只希望明确声明所有的Maven配置。

如果您不想使用spring-boot-starter-parent，则仍然可以通过使用scope=import依赖来保持依赖管理（但不能进行插件管理）的好处：
```
<dependencyManagement>
     <dependencies>
        <dependency>
            <!-- Import dependency management from Spring Boot -->
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>1.5.2.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```
该设置不允许您使用如13.2.1 所述的属性来覆盖单个依赖关系。 要实现相同的结果，您需要在spring-boot-dependencies条目之前在项目的dependencyManagement中添加一个条目。 例如，要升级到另一个Spring Data发行版本，您需要将以下内容添加到您的pom.xml中。
```
<dependencyManagement>
    <dependencies>
        <!-- Override Spring Data release train provided by Spring Boot -->
        <dependency>
            <groupId>org.springframework.data</groupId>
            <artifactId>spring-data-releasetrain</artifactId>
            <version>Fowler-SR2</version>
            <scope>import</scope>
            <type>pom</type>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>1.5.2.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
```
    >在上面的例子中，我们指定了一个BOM，但是任何依赖关系类型都可以被这样覆盖。