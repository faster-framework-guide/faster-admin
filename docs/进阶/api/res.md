# 响应

接口的响应分为两种，成功与失败。

其中成功的响应我们直接使用http的body体作为内容，并没有为其包装额外的接口定义，我们认为这是多余的（最起码在现在看来）。

而失败的响应，我们定义了包装体，并返回失败的http状态码如400，内容格式如下：

```
{
    "timestamp":1499404172029,//请求时间戳
    "status":400,//http状态码
    "path":"",//请求路径
    "code":"2",//业务状态码
    "message":"nickname不能为空"//错误信息
}
```

我们可以使用ResponseErrorEntity.error()返回错误信息。
```
return ResponseErrorEntity.error(SysPermissionError.PERMISSION_CODE_EXIST, HttpStatus.BAD_REQUEST);
```

或者

```
return ResponseErrorEntity.error("错误信息", HttpStatus.BAD_REQUEST);
```

我们也可以直接抛出异常：

```
BasicErrorCode.DISCARD_ERROR.throwException();
```

其中BasicErrorCode是我们定义的枚举类状态码，我们要求状态码必须实现ErrorCode接口，我们可以根据业务定义自己的ErrorCode，BasicErrorCode代码如下：

```
package cn.org.faster.framework.web.exception.model;

/**
 * @author zhangbowen
 */
public enum BasicErrorCode implements ErrorCode {
    ERROR(1000, "处理失败"),
    PARAM_ERROR(1001, "参数异常"),
    TOKEN_INVALID(1002, "登录状态过期"),
    SMS_SEND_ERROR(1003, "短信发送失败"),
    DISCARD_ERROR(1005, "版本过时"),
    PERMISSION_ERROR(1006, "权限不足"),
    SERVER_ERROR(1007, "服务器正在维护"),
    ;

    private int value;
    private String description;

    BasicErrorCode() {
    }

    BasicErrorCode(int value, String description) {
        this.value = value;
        this.description = description;
    }

    @Override
    public int getValue() {
        return this.value;
    }

    @Override
    public String getDescription() {
        return this.description;
    }
}

```