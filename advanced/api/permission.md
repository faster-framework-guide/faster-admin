# 权限

使用shiro权限框架来处理接口的访问权限，每个用户拥有角色，每个角色拥有权限。

在接口端我们需要定义访问某个接口所必须的权限，使用@RequiresPermissions注解。

下面的示例定义了访问video添加接口时，所需要video:add权限。
这个权限code在权限管理中定义，然后在角色管理中为角色选择这个权限，最后用户会被分配某个角色，这样用户与权限的关系便绑定在了一起。

```
    /**
     * 新增视频
     *
     * @param request 请求参数
     * @return ResponseEntity
     */
    @PostMapping
    @RequiresPermissions("video:add")
    public ResponseEntity add(@Validated @RequestBody VideoAddRequest request) {
        Video video = new Video();
        BeanUtils.copyProperties(request, video);
        return videoService.add(video);
    }
```