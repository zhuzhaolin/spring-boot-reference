### 20.2.6 已知的限制

重新启动功能对于使用标准ObjectInputStream反序列化的对象无效。 如果需要反序列化数据，可能需要使用Spring的ConfigurableObjectInputStream与Thread.currentThread()。getContextClassLoader()组合使用。

不幸的是，几个第三方库在不考虑上下文类加载器的情况下反序列化。 如果您发现这样的问题，您需要向原始作者请求修复。