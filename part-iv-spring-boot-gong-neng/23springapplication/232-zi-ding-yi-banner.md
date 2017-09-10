### 23.2 自定义Banner

可以通过在您的类路径中添加一个 banner.txt 文件，或者将banner.location设置到banner文件的位置来更改启动时打印的banner。 如果文件有一些不常用的编码，你可以设置banner.charset（默认为UTF-8）。除了文本文件，您还可以将banner.gif，banner.jpg或banner.png图像文件添加到您的类路径中，或者设置一个banner.image.location属性。 图像将被转换成ASCII艺术表现，并打印在任何文字banner上方。

您可以在banner.txt文件中使用以下占位符：

**表23.1. banner变量**

| 变量名 | 描述 |
| :---: | :---: |
| ${application.version} | 在MANIFEST.MF中声明的应用程序的版本号。例如， Implementation-Version: 1.0 被打印为 1.0. |
| ${application.formatted-version} | 在MANIFEST.MF中声明的应用程序版本号的格式化显示（用括号括起来，以v为前缀）。 例如 \(v1.0\)。 |
| ${spring-boot.version} | 您正在使用的Spring Boot版本。 例如1.5.2.RELEASE。 |
| ${spring-boot.formatted-version} | 您正在使用格式化显示的Spring Boot版本（用括号括起来，以v为前缀）。 例如（v1.5.2.RELEASE）。 |
| ${Ansi.NAME} \(or ${AnsiColor.NAME}, ${AnsiBackground.NAME}, ${AnsiStyle.NAME}\) | 其中NAME是ANSI转义码的名称。 有关详细信息，请参阅 AnsiPropertySource。 |
| ${application.title} | 您的应用程序的标题在MANIFEST.MF中声明。 例如Implementation-Title：MyApp打印为MyApp。 |

    >如果要以编程方式生成banner，则可以使用SpringApplication.setBanner()方法。 使用org.springframework.boot.Banner 如接口，并实现自己的printBanner() 方法。
    
您还可以使用spring.main.banner-mode属性来决定是否必须在System.out（控制台）上打印banner，使用配置的logger（log）或不打印（off）。    



