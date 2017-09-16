### 20.2.2 监视额外的路径

有时当您对不在类路径中的文件进行更改时，需要重新启动或重新加载应用程序。为此，请使用spring.devtools.restart.additional-paths属性来配置其他路径以监视更改。 您可以使用上述的spring.devtools.restart.exclude属性来控制附加路径下的更改是否会触发完全重新启动或只是[实时重新加载](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools-livereload)。