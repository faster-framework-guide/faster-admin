# 参数检验

我们使用Spring的Valided框架用于接口的参数检验，使用非常简单，仅需要在接口方法中需要检验的bean前面增加@Validated即可。

检验规则在Bean中定义。

示例如下：


使用@Validated注解定义Request实体。

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


使用@NotBlank注解标识name字段不能为空。

```
package com.admin.modules.video.model.request;

import lombok.Data;
import cn.org.faster.framework.mybatis.entity.BaseEntity;
import lombok.EqualsAndHashCode;
import javax.validation.constraints.NotBlank;

/**
 * @author faster-builder
 * 视频 request
 */
@Data
@EqualsAndHashCode(callSuper = true)
public class VideoAddRequest extends BaseEntity{
    /**
     * 标题
     * 使用@NotBlank注解标识name字段不能为空。
     */
    @NotBlank
    private String name;
}
```