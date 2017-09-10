### 20.2.4 使用触发文件

如果您使用IDE工具编写代码，更改文件，则您可能希望仅在特定时间触发重新启动。 为此，您可以使用“触发文件”，这是一个特殊文件，当您要实际触发重新启动检查时，必须修改它。 更改文件只会触发检查，只有在Devtools检测到它必须执行某些操作时才会重新启动。 触发文件可以手动更新，也可以通过IDE插件更新。

要使用触发器文件，请使用spring.devtools.restart.trigger-file属性。

    >您可能希望将spring.devtools.restart.trigger-file设置为[全局设置](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools-globalsettings)，以使所有项目的行为方式相同。