### 20.2 自动重启

使用spring-boot-devtools的应用程序将在类路径上的文件发生更改时自动重新启动。 这在IDE中开发时可能是一个有用的功能，因为它为代码更改提供了非常快的反馈循环。 默认情况下，将监视指向文件夹的类路径上的任何条目。 请注意，某些资源（如静态资源和视图模板）不需要重新启动应用程序。

**触发重启**
当DevTools监视类路径资源时，触发重新启动的唯一方法是更新类路径中的文件时。 导致类路径更新的方式取决于您正在使用的IDE。 在Eclipse中，保存修改的文件将导致类路径被更新并触发重新启动。 在IntelliJ IDEA中，构建项目（Build→Make Project）将具有相同的效果。

    >只要 forking 被启用，您也可以通过支持的构建插件（即Maven和Gradle）启动应用程序，因为DevTools需要一个单独的应用程序类加载器才能正常运行。Gradle和Maven默认情况下在类路径上检DevTools。

    >自动重启当与LiveReload一起使用时工作非常好。 详见[下文](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-boot-devtools-livereload)。 如果您使用JRebel，自动重启将被禁用，有利于动态类重新加载。 其他devtools功能仍然可以使用（如LiveReload和属性覆盖）。

    >DevTools依赖于应用程序上下文的关闭钩子，以在重新启动期间关闭它。 如果禁用了关闭挂钩（SpringApplication.setRegisterShutdownHook（false）），DevTools将无法正常工作。

    >当判断类路径中的项目是否会在更改时触发重新启动时，DevTools会自动忽略名为spring-boot，spring-boot-devtools，spring-boot-autoconfigure，spring-boot-actuator和spring-boot-start的项目。

**重新启动(Restart) vs 重新加载(Reload)**

Spring Boot提供的重新启动技术使用两个类加载器。 不会改的类（例如，来自第三方的jar）被加载到基类加载器中。 您正在开发的类被加载到重新启动(restart)类加载器中。 当应用程序重新启动时，重新启动类加载器将被丢弃，并创建一个新的类加载器。 这种方法意味着应用程序重新启动通常比“冷启动”快得多，因为基类加载器已经可以使用

如果发现重新启动对应用程序不够快，或遇到类加载问题，您可以考虑来自ZeroTurnaround的JRebel等重新加载技术。 这些工作通过在加载类时重写(rewriting)类，使其更适合重新加载。 Spring Loaded提供了另一个选项，但是它在很多框架上不支持，并且不支持商用。