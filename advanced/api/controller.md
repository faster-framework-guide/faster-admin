# Controller

controller层我们一般用来对外提供接口，其实本质是对SpringMvc的使用，我们可以在这一层为接口增加权限，参数检验等功能。


路径：/src/main/java/你的根包/modules/你的业务名/controller
文件：业务名Controller.java

我们使用Shiro的注解@RequiresPermissions设置权限，其内容在权限管理中配置。

下面是一个controller示例：

```
package com.admin.modules.video.controller;

import java.util.List;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.*;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.validation.annotation.Validated;
import org.springframework.beans.BeanUtils;
import org.apache.shiro.authz.annotation.RequiresPermissions;
import com.admin.modules.video.service.VideoService;
import com.admin.modules.video.model.request.VideoAddRequest;
import com.admin.modules.video.model.request.VideoQueryRequest;
import com.admin.modules.video.model.request.VideoListRequest;
import com.admin.modules.video.model.request.VideoUpdateRequest;
import com.admin.modules.video.entity.Video;

/**
 * @author faster-builder
 * 视频 Controller
 */
@RestController
@RequestMapping("/video")
public class VideoController {
    @Autowired
    private VideoService videoService;

    /**
     * 视频分页列表
     *
     * @param request 视频实体
     * @return ResponseEntity
     */
    @GetMapping
    @RequiresPermissions("video:list")
    public ResponseEntity list(VideoListRequest request) {
        Video video = new Video();
        BeanUtils.copyProperties(request, video);
        return ResponseEntity.ok(videoService.list(video));
    }

    /**
     * 视频根据id查询详情
     *
     * @param id 主键id
     * @return ResponseEntity
     */
    @GetMapping("/{id}")
    @RequiresPermissions("video:info")
    public ResponseEntity queryById(@PathVariable Long id) {
        return ResponseEntity.ok(videoService.getById(id));
    }

    /**
     * 视频根据条件查询详情
     *
     * @return ResponseEntity
     */
    @GetMapping("/query")
    @RequiresPermissions("video:info")
    public ResponseEntity query(VideoQueryRequest request) {
        Video video = new Video();
        BeanUtils.copyProperties(request, video);
        return ResponseEntity.ok(videoService.query(video));
    }

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

    /**
     * 更新视频
     *
     * @param request 请求参数
     * @param id 主键id
     * @return ResponseEntity
     */
    @PutMapping("/{id}")
    @RequiresPermissions("video:modify")
    public ResponseEntity update(@PathVariable Long id,@RequestBody VideoUpdateRequest request) {
        Video video = new Video();
        BeanUtils.copyProperties(request, video);
        video.setId(id);
        return videoService.update(video);
    }

    /**
     * 删除视频
     *
     * @param id 主键id
     * @return ResponseEntity
     */
    @DeleteMapping("/delete")
    @RequiresPermissions("video:delete")
    public ResponseEntity delete(@RequestBody List<Long>  ids) {
        ids.forEach(item -> {
            if (item == 0L) {
                return;
            }
            videoService.delete(item);
        });
        return new ResponseEntity(HttpStatus.NO_CONTENT);
    }
}
```