### 11.4 运行示例

由于我们使用了spring-boot-starter-parent POM，所以我们有一个可用的运行目标，我们可以使用它来启动应用程序。 键入mvn spring-boot：从根目录运行以启动应用程序：
```
$ mvn spring-boot:run
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::  (v1.5.2.RELEASE)
....... . . .
....... . . . (log output here)
....... . . .
........ Started Example in 2.222 seconds (JVM running for 6.514)
```

如果你用浏览器打开 http://localhost:8080 你应该看到以下输出：

```
Hello World!
```
ctrl-c 正常(gracefully)退出应用程序。