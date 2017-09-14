### 20.2.3 禁用重启

如果不想使用重新启动功能，可以使用spring.devtools.restart.enabled属性来禁用它。 在大多数情况下，您可以在application.properties中设置此项（这仍将初始化重新启动类加载器，但不会监视文件更改）。

例如，如果您需要完全禁用重新启动支持，因为它在一些特定库中不能正常运行，则需要在调用SpringApplication.run（…）之前设置System属性。 例如：
```
public static void main(String[] args) {
    System.setProperty("spring.devtools.restart.enabled", "false");
    SpringApplication.run(MyApp.class, args);
}
```