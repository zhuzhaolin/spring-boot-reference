### 11. 开发您的第一个Spring Boot应用程序

让我们在Java中开发一个简单的“Hello World！”Web应用程序，突显Spring Boot一些主要的功能。 我们将使用Maven构建该项目，因为大多数IDE支持它。
>https://spring.io/ 包含许多使用Spring Boot的“入门指南”。 如果您正在寻求解决一些具体问题; 可以先看一下那里。

您可以在 https://start.spring.io/ 的依赖关系搜索器中选择Web启动器来快速完成以下步骤。
这会自动生成一个新的项目结构，方便您立即[开始编码](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#getting-started-first-application-code)。 查看文档了解[更多详细信息](https://github.com/spring-io/initializr)。

在开始之前，打开终端来检查您是否安装了有效的Java和Maven版本。
```
$ java -version
java version "1.7.0_51"
Java(TM) SE Runtime Environment (build 1.7.0_51-b13)
Java HotSpot(TM) 64-Bit Server VM (build 24.51-b03, mixed mode)
$ mvn -v
Apache Maven 3.2.3 (33f8c3e1027c3ddde99d3cdebad2656a31e8fdf4; 2014-08-11T13:58:10-07:00)
Maven home: /Users/user/tools/apache-maven-3.1.1
Java version: 1.7.0_51, vendor: Oracle Corporation
```
>这个示例需要在其自己的文件夹中创建。 后面我们假设您在当前目录已经创建了一个正确的文件夹。
