# Node.js

Node.js 是一个基于 Chrome V8 引擎的 JavaScript 运行环境。 Node.js 使用了一个事件驱动、非阻塞式 I/O 的模型，使其轻量又高效。 Node.js 的包管理器 npm，是全球最大的开源库生态系统。 Faster-Admin-Web同样使用NPM作为包管理。

## 下载安装

[下载地址](https://nodejs.org/en/)

下载LTS版本，之后安装即可。

## 验证安装

打开终端，输入以下命令：

```
node -v
```

出现版本号即为安装成功

## 镜像源设置

node.js中使用npm进行管理依赖，由于npm默认为国外仓库，我们修改为淘宝镜像源以加速下载依赖。

打开终端，输入以下命令：

```
npm config set registry https://registry.npm.taobao.org
```

验证：

```
npm config get registry
```

出现taobao的镜像源地址即为成功

## 总结

至此，我们的Node.js安装配置完毕。