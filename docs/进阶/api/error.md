# 错误处理

Faster-Framework框架底层已经拦截了大多数异常，并且在遇到异常时包装了返回消息，我们无须在程序内部使用try catch进行拦截。

并且我们可以使用直接抛出异常的方式来处理业务，如下：

使用状态码抛出异常：

```
BasicErrorCode.DISCARD_ERROR.throwException();
```

或直接抛出异常：

```
throw BusinessException.build(10000,"数据已被删除");
```

