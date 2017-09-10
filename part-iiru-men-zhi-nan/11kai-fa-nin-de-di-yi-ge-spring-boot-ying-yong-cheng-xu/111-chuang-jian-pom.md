### 11.1 创建POM

我们需要先创建一个Maven pom.xml文件。 pom.xml是用于构建项目的配置文件。打开编辑器并添加以下内容：
```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>myproject</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.2.RELEASE</version>
    </parent>
    <!-- Additional lines to be added here... -->
</project>
```
这应该给你一个工作构建(working build)，你可以通过运行 mvn package 进行测试（你可以暂时忽略警告：“jar will be empty - no content was marked for inclusion!”）。
>现在，您可以将项目导入到IDE中（最新的Java IDE内置对Maven的支持）。 为了简单起见，这个示例我们继续使用纯文本编辑器。