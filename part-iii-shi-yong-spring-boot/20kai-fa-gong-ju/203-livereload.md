### 20.3 LiveReload

spring-boot-devtools模块包括一个嵌入式LiveReload服务器，可以在资源更改时用于触发浏览器刷新。 LiveReload浏览器扩展程序可以从 http://livereload.com 免费获取Chrome，Firefox和Safari的插件。

如果您不想在应用程序运行时启动LiveReload服务器，则可以将spring.devtools.livereload.enabled属性设置为false。

    >一次只能运行一个LiveReload服务器。 开始应用程序之前，请确保没有其他LiveReload服务器正在运行。 如果从IDE启动多个应用程序，则只有第一个应用程序将支持LiveReload。