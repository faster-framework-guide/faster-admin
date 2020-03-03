# 网络请求

我们使用umi官方推荐的网络工具进行网络请求。

引入：

```
import request from '@/common/utils/request';
```

使用：

```
request.post('/goods',  { data: values }).then(res => {
        //提交成功
        modal.hideAndRefresh();
});
```

更多使用方式查看：

https://github.com/umijs/umi-request