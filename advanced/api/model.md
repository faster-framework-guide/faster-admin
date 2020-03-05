# Model

model包下的类主要针对特定接口的请求和返回而创建的，默认情况下，代码生成器会生成增删改查四个请求类，而对于我们后台代码来说，一般情况下返回值为实体。

路径：/src/main/java/你的根包/modules/你的业务名/model
文件：业务名AddRequest.java、业务名ListRequest.java等

示例：

```
package com.admin.modules.video.model.request;

import lombok.Data;
import cn.org.faster.framework.mybatis.entity.BaseEntity;
import lombok.EqualsAndHashCode;

/**
 * @author faster-builder
 * 视频 request
 */
@Data
@EqualsAndHashCode(callSuper = true)
public class VideoAddRequest extends BaseEntity{
    /**
     * 分类id
     */
    private Long categoryId;
    /**
     * 标题
     */
    private String name;
    /**
     * url地址
     */
    private String url;
    /**
     * 封面图片
     */
    private String img;
    /**
     * 内容
     */
    private String content;
    /**
     * 时长
     */
    private Integer time;
    /**
     * 学科id
     */
    private Long subjectId;
}
```

使用：

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