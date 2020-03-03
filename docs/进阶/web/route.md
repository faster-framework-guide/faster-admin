# 路由

列表、新增、编辑页面完成以后，便是添加路由。

我们需要在router-modules.js中增加业务页面的路由，如下：

```
const routes = [
  {
    path: '/video',
    name:'视频管理',
    component: './video',
    authority: 'video:manage',
    icon: 'smile'
  },
];

export default routes;
```

我们仅需要在routes数组下增加即可。

path：代表请求页面的路径。
name：表示页面名称，如果只有一层，该路由会在菜单中展示，name展示的便是菜单的名称。
component：指向的是刚才我们编写的模块包名，根路径从pages开始。
authority：代表我们访问这个路由或者这个菜单是否展示所需要的权限编码，可以在权限管理中进行配置。


路由可以配置多级，如下：

```
 {
    path: '/sys',
    name: '系统管理',
    icon: 'setting',
    routes: [
      {
        path: '/user',
        name: '用户管理',
        icon: 'user',
        authority:"users:manage",
        component: '../common/pages/sys/user'
      }
}
```
