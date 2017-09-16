### 20.2.5 自定义重新启动类加载器

如上面的 [Restart vs Reload](http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-spring-boot-restart-vs-reload) 部分所述，重新启动功能是通过使用两个类加载器实现的。 对于大多数应用程序，此方法运行良好，但有时可能会导致类加载问题。

默认情况下，IDE中的任何打开的项目将使用“重新启动”类加载器加载，任何常规.jar文件将使用“base”类加载器加载。 如果您在多模块项目上工作，而不是每个模块都导入到IDE中，则可能需要自定义事件。 为此，您可以创建一个META-INF / spring-devtools.properties文件。

spring-devtools.properties文件可以包含restart.exclude 和 restart.include.prefixed属性。 include元素是应该被拉入“重新启动(restart)”类加载器的项目，排除元素是应该向下推入“基本(base)”类加载器的项目。 属性的值是将应用于类路径的正则表达式模式。

例如：
```
http://docs.spring.io/spring-boot/docs/1.5.2.RELEASE/reference/htmlsingle/#using-spring-boot-restart-vs-reload
```

    >所有属性键必须是唯一的。 只要一个属性从restart.include. 或restart.exclude. 开始，将被考虑。

    >将加载类路径中的所有META-INF/spring-devtools.properties。 您可以在项目中打包文件，或者在项目所使用的库中打包文件