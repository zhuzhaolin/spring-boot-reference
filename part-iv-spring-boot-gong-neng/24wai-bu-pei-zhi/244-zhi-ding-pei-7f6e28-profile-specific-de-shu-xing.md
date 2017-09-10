### 24.4 指定配置(Profile-specific)的属性

除了application.properties文件外，还可以使用命名约定application- {profile}.properties定义的指定配置文件。 环境具有一组默认配置文件，如果没有设置活动配置文件（即，如果没有显式激活配置文件，则加载了来自application-default.properties的属性）。

指定配置文件（Profile-specific）的属性从与标准application.properties相同的位置加载，指定配置( profile-specific)文件始终覆盖非指定文件，而不管指定配置文件是否在打包的jar内部或外部。

如果有几个指定配置文件，则应用最后一个配置。 例如，由spring.profiles.active属性指定的配置文件在通过SpringApplication API配置的配置之后添加，因此优先级高。

    >如果您在spring.config.location中指定了任何文件，则不会考虑这些特定配置(profile-specific)文件的变体。 如果您还想使用指定配置(profile-specific)文件的属性，请使用spring.config.location中的目录。