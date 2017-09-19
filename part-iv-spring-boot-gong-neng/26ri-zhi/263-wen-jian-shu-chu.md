### 26.3 文件输出

默认情况下，Spring Boot将仅将日志输出到控制台，不会写到文件。 如果要将控制台上的日志输出到日志文件，则需要设置logging.file或logging.path属性（例如在application.properties中）。

下表显示了如何一起使用logging.\*属性：

**表26.1 Logging属性**

| logging.file | logging.path | Example | 	Description |
| :--- | :--- | :--- | :--- |
| (none) | (none) |  | 	仅控制台输出 |
| Specific file | (none) | my.log | 写入指定的日志文件。 名称可以是确切的位置或相对于当前目录。 |
| (none) | Specific directory | /var/log | 将spring.log写入指定的目录。 名称可以是确切的位置或相对于当前目录。 |

日志文件将在10 MB时滚动输出到文件，默认情况下会记录控制台输出，ERROR，WARN和INFO级别的消息。


    >日志记录系统在应用程序生命周期早期初始化，并且在通过@PropertySource注解加载的属性文件中将不会找到log属性。

    >日志属性独立于实际的日志记录基础结构。 因此，特定配置key（如Logback的logback.configurationFile）不受Spring Boot管理。