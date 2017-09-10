### 10.2.5 命令行提示

Spring Boot CLI为BASH和zsh shell提供命令提示的功能。 您可以在任何shell中引用脚本（也称为spring），或将其放在您的个人或系统范围的bash完成初始化中。 在Debian系统上，系统范围的脚本位于 /shell-completion/bash 中，当新的shell启动时，该目录中的所有脚本将被执行。 手动运行脚本，例如 如果您使用SDKMAN安装了！
```
$ . ~/.sdkman/candidates/springboot/current/shell-completion/bash/spring
$ spring <HIT TAB HERE>
  grab  help  jar  run  test  version
  ```
  >如果使用Homebrew或MacPorts安装Spring Boot CLI，则命令行补全脚本将自动注册到您的shell。