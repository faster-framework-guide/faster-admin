# 基本流程

下面这张图清晰的展现了我们新增一个页面功能所需要做的工作。

```flow
st=>start: 新建模块包
e=>end: 配置权限
index=>operation: 新建列表页面
add=>operation: 新建新增页面
edit=>operation: 新建编辑页面
route=>operation: router-modules中新增路由

st->index->add->edit->route->e
```
