### 26.2.1 日志颜色输出

如果您的终端支持ANSI，颜色输出可以增加可读性。 您可以将spring.output.ansi.enabled设置为支持的值来覆盖自动检测。

使用％clr关键字配置颜色编码。 在最简单的形式下，转换器将根据日志级别对输出进行着色，例如：
```
%clr(%5p)
```

日志级别映射到颜色如下：

    + blue
    + cyan
    + faint
    + green
    + magenta
    + red
    + yellow