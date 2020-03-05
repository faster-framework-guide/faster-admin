# 配置

config目录下包含前端所有的配置文件。
一般来说我们仅仅需要：
编辑router-modules.js修改路由。
编辑config.dev.js、config.test.js、config、prod.js修改接口地址或增加自己的基于环境不同的配置。
编辑defaultSettings.js修改系统的标题、描述、版权信息。


utils目录下的request.js为我们针对umi官方的网络请求所进行的二次包装，以满足我们自身业务接口的需要，如果有需要也可以进行修改。