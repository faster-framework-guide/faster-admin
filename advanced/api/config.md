# 配置

代码生成器已经为我们内置好了一些常用的配置，一般来说，我们仅仅需要修改数据库的相关信息，文件上传存储的路径即可。

针对不同的环境，我们需要修改不同的文件：

application-local.yml（本地环境）
application-dev.yml（开发环境）
application-test.yml（测试环境）
application-prod.yml（生产环境）

示例如下：

```
app:
  datasource:
    name: faster-admin-test
    host: 127.0.0.1
    port: 3306
    username: root
    password: 123456
  upload:
    local:
      file-dir: /data/upload/faster-admin-test
      url-prefix: http://127.0.0.1:8080
```

如果在windows环境下，file-dir需要按照windows的目录格式进行设置。
