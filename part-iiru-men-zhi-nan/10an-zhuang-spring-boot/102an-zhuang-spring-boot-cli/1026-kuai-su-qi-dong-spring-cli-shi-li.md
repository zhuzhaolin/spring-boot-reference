### 10.2.6 快速启动Spring CLI示例

这是一个非常简单的Web应用程序，可用于测试您的安装是否正确。 创建一个名为app.groovy的文件：
```
@RestController
class ThisWillActuallyRun {
    @RequestMapping("/")
    String home() {
        "Hello World!"
    }
}
```
然后从shell运行它：
```
$ spring run app.groovy
```
因为下载依赖的库，首次运行应用程序需要一些时间，。 后续运行将会更快。

在浏览器中打开 http://localhost:8080 ，您应该会看到以下输出：
```
Hello World!
```