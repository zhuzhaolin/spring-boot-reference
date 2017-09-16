### 20.4 全局设置

您可以通过向 $HOME 文件夹添加名为.spring-boot-devtools.properties的文件来配置全局devtools设置（请注意文件名以“.”开头）。 添加到此文件的任何属性将适用于您的计算机上使用devtools的所有Spring Boot应用程序。 例如，要配置重新启动以始终使用触发器文件，您可以添加以下内容：

~/.spring-boot-devtools.properties.

```
spring.devtools.reload.trigger-file=.reloadtrigger
```