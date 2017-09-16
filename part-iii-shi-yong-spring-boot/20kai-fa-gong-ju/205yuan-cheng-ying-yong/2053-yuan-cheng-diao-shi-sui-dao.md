### 20.5.3 远程调试隧道

在远程应用程序诊断问题时，Java远程调试非常有用。 不幸的是，当您的应用程序部署在数据中心之外时，并不总是能够进行远程调试。 如果您正在使用基于容器的技术（如Docker），远程调试也可能难以设置。

为了帮助解决这些限制，devtools支持基于HTTP隧道的传输远程调试传输。 远程客户端在端口8000上提供本地服务器，您可以连接远程调试器。 建立连接后，通过HTTP将调试数据发送到远程应用程序。 如果要使用其他端口，可以使用spring.devtools.remote.debug.local-port属性更改。

您需要确保远程应用程序启用远程调试启用。 通常可以通过配置JAVA_OPTS来实现。 例如，使用Cloud Foundry，您可以将以下内容添加到manifest.yml中：

```
---
    env:
        JAVA_OPTS: "-Xdebug -Xrunjdwp:server=y,transport=dt_socket,suspend=n"
```

    >请注意，您不需要将 address=NNNN 选项传递给-Xrunjdwp。 如果省略Java将随机选择一个的空闲端口。

    >通过网络调试远程服务可能很慢，您可能需要在IDE中增加超时时间。 例如，在Eclipse中，您可以从Preferences…中选择Java→Debug ，并将Debugger timeout (ms)更改为更合适的值（大多数情况下，60000可以正常工作）。

    >当使用IntelliJ IDEA的远程调试隧道时，必须将所有调试断点配置为挂起线程而不是挂起VM。 默认情况下，IntelliJ IDEA中的断点会挂起整个VM，而不是仅挂起触发断点的线程。 这会导致挂起管理远程调试通道的线程等不必要的副作用，导致调试会话冻结。 当使用IntelliJ IDEA的远程调试隧道时，应将所有断点配置为挂起线程而不是VM。 有关详细信息，请参阅[IDEA-165769](https://youtrack.jetbrains.com/issue/IDEA-165769)。