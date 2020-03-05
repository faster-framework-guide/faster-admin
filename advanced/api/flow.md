# 基本流程

下面这张图清晰的展现了我们新增一个功能所需要做的工作。

```flow
st=>start: 设计数据库
e=>end: 创建Controller
entity=>operation: 创建实体类
mapper=>operation: 创建Mapper
service=>operation: 创建Service
model=>operation: 创建Model

st->entity->mapper->service->model->e
```
