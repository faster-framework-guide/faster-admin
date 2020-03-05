# 总体结构

如果您按照快速启动或者代码生成器导入项目，那么整个后端项目的基本结构及说明如下：

```
├── db                    #后端基本数据表设计 
├── src
│   ├── main 
│   │   ├── java 
│   │   │   ├── cn.org.faster.framework.admin   # 后台管理端核心代码包
│   │   │   ├── xxx.xxx
│   │   │   │   ├── modules                     # 代码生成器生成的业务模块代码
│   │   │   │   │   ├── video 
│   │   │   │   │   │   ├── controller          # 接口定义层，定义接口、参数、权限。
│   │   │   │   │   │   ├── entity              # 实体
│   │   │   │   │   │   ├── mapper              # mybatis接口定义
│   │   │   │   │   │   ├── model               # 请求响应模型包
│   │   │   │   │   │   ├── service             # 业务处理层，默认生成基本的增删改查
│   │   │   │   ├── Application.java            # 项目启动入口
│   │   ├── resources 
│   ├── test 
│   │   ├── java
│   │   │   ├── xxx.xxx.test                    # 单元测试包
│   │   │   │   ├── modules   
│   └── └── └── └── BaseTest.java               # 单元测试基础父类试基础父类
├── .gitignore               # git忽略文件
└── pom.xml                  # maven依赖管理文件
```