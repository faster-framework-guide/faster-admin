# 总体结构

如果您按照快速启动或者代码生成器导入项目，那么整个前端项目的基本结构及说明如下：

```
├── config              
│   ├── config.dev.js       # 开发环境配置文件
│   ├── config.js           # 全局配置文件，会与环境配置文件合并
│   ├── config.prod.js      # 生产环境配置文件
│   ├── config.test.js      # 测试环境配置文件
│   ├── defaultSettings.js  # 默认常量设置
│   ├── plugin.config.js    # 插件设置
│   ├── router-modules.js   # 业务路由设置
│   ├── router.js           # 默认路由设置
├── mock                    # mock文件夹，模拟、拦截接口数据使用    
├── public
│   ├── favicon.png         # 网站头像，展示在浏览器标题旁
├── src
│   ├── common
│   │   ├── components      # 通用组件
│   │   ├── layouts         # 通用布局
│   │   ├── pages           # 系统页面
│   │   ├── utils           # 工具包
│   │   ├── logo.png        # 网站logo
│   ├── models
│   ├── pages
│   │   ├── demo                # 示例包，通过npm run mock启动
│   │   ├── video           
│   │   │   ├── index.jsx       # 视频列表页
│   │   │   ├── VideoAdd.jsx    # 视频添加页
│   │   │   ├── VideoEdit.jsx   # 视频编辑页
│   │   ├── Dashboard.jsx       # 控制台页面
│   └── └── document.ejs        # umi 约定如果这个文件存在，会作为默认模板，内容上需要保证有
├── .editorconfig               # 编辑器的格式化文件，需要安装editor插件
├── .gitignore               # git忽略文件
├── jsconfig.json               # 表示该目录是JavaScript项目的根目录以及相关功能
└── package.json                  # npm依赖管理文件
```