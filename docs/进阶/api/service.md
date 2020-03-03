# Service

接下来我们需要创建Service来调用我们的Mapper,并且编写我们的业务逻辑.

我们可以继承ServiceImpl类。来初始化一些常用的方法。

路径：/src/main/java/你的根包/modules/你的业务名/service
文件：业务名Service.java

例子：

```
package com.admin.modules.video.service;

import com.baomidou.mybatisplus.core.metadata.IPage;
import org.springframework.util.StringUtils;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.stereotype.Service;
import org.springframework.transaction.annotation.Transactional;
import com.baomidou.mybatisplus.core.conditions.query.LambdaQueryWrapper;
import com.baomidou.mybatisplus.extension.service.impl.ServiceImpl;
import com.admin.modules.video.mapper.VideoMapper;
import com.admin.modules.video.entity.Video;

/**
 * @author faster-builder
 * 视频 Service
 */
@Service
@Transactional
public class VideoService extends ServiceImpl<VideoMapper, Video> {

    /**
     * 分页查询
     * @param video 请求参数
     * @return 视频分页列表
     */
    public IPage<Video> list(Video video) {
        LambdaQueryWrapper<Video> queryWrapper = new LambdaQueryWrapper<>();
        if (video.getId() != null) {
            queryWrapper.eq(Video::getId, video.getId());
        }
        if (video.getCategoryId() != null) {
            queryWrapper.eq(Video::getCategoryId, video.getCategoryId());
        }
        if (!StringUtils.isEmpty(video.getName())) {
            queryWrapper.eq(Video::getName, video.getName());
        }
        if (!StringUtils.isEmpty(video.getUrl())) {
            queryWrapper.eq(Video::getUrl, video.getUrl());
        }
        if (!StringUtils.isEmpty(video.getImg())) {
            queryWrapper.eq(Video::getImg, video.getImg());
        }
        if (!StringUtils.isEmpty(video.getContent())) {
            queryWrapper.eq(Video::getContent, video.getContent());
        }
        if (video.getTime() != null) {
            queryWrapper.eq(Video::getTime, video.getTime());
        }
        if (video.getCreateBy() != null) {
            queryWrapper.eq(Video::getCreateBy, video.getCreateBy());
        }
        if (video.getUpdateBy() != null) {
            queryWrapper.eq(Video::getUpdateBy, video.getUpdateBy());
        }
        if (video.getCreateDate() != null) {
            queryWrapper.eq(Video::getCreateDate, video.getCreateDate());
        }
        if (video.getUpdateDate() != null) {
            queryWrapper.eq(Video::getUpdateDate, video.getUpdateDate());
        }
        if (video.getSort() != null) {
            queryWrapper.eq(Video::getSort, video.getSort());
        }
        if (!StringUtils.isEmpty(video.getRemark())) {
            queryWrapper.eq(Video::getRemark, video.getRemark());
        }
        if (video.getDeleted() != null) {
            queryWrapper.eq(Video::getDeleted, video.getDeleted());
        }
        if (video.getSubjectId() != null) {
            queryWrapper.eq(Video::getSubjectId, video.getSubjectId());
        }
        queryWrapper.orderByDesc(Video::getCreateDate);
        return super.baseMapper.selectPage(video.toPage(), queryWrapper);
    }

    /**
     * 根据条件查询详情
     * @param video 请求参数
     * @return 视频详情
     */
    public Video query(Video video) {
        LambdaQueryWrapper<Video> queryWrapper = new LambdaQueryWrapper<>();
        if (video.getId() != null) {
            queryWrapper.eq(Video::getId, video.getId());
        }
        if (video.getCategoryId() != null) {
            queryWrapper.eq(Video::getCategoryId, video.getCategoryId());
        }
        if (!StringUtils.isEmpty(video.getName())) {
            queryWrapper.eq(Video::getName, video.getName());
        }
        if (!StringUtils.isEmpty(video.getUrl())) {
            queryWrapper.eq(Video::getUrl, video.getUrl());
        }
        if (!StringUtils.isEmpty(video.getImg())) {
            queryWrapper.eq(Video::getImg, video.getImg());
        }
        if (!StringUtils.isEmpty(video.getContent())) {
            queryWrapper.eq(Video::getContent, video.getContent());
        }
        if (video.getTime() != null) {
            queryWrapper.eq(Video::getTime, video.getTime());
        }
        if (video.getCreateBy() != null) {
            queryWrapper.eq(Video::getCreateBy, video.getCreateBy());
        }
        if (video.getUpdateBy() != null) {
            queryWrapper.eq(Video::getUpdateBy, video.getUpdateBy());
        }
        if (video.getCreateDate() != null) {
            queryWrapper.eq(Video::getCreateDate, video.getCreateDate());
        }
        if (video.getUpdateDate() != null) {
            queryWrapper.eq(Video::getUpdateDate, video.getUpdateDate());
        }
        if (video.getSort() != null) {
            queryWrapper.eq(Video::getSort, video.getSort());
        }
        if (!StringUtils.isEmpty(video.getRemark())) {
            queryWrapper.eq(Video::getRemark, video.getRemark());
        }
        if (video.getDeleted() != null) {
            queryWrapper.eq(Video::getDeleted, video.getDeleted());
        }
        if (video.getSubjectId() != null) {
            queryWrapper.eq(Video::getSubjectId, video.getSubjectId());
        }
        return super.getOne(queryWrapper);
    }

     /**
     * 根据主键id查询详情
     * @param id 视频id
     * @return 视频详情
     */
    public Video queryById(Long id) {
        return super.getById(id);
    }

    /**
    * 添加视频
    * @param video 实体
    * @return ResponseEntity
    */
    public ResponseEntity add(Video video) {
        video.preInsert();
        super.save(video);
        return new ResponseEntity(HttpStatus.CREATED);
    }

    /**
    * 修改视频
    * @param video 实体
    * @return ResponseEntity
    */
    public ResponseEntity update(Video video) {
        video.preUpdate();
        super.updateById(video);
        return new ResponseEntity(HttpStatus.CREATED);
    }

    /**
     * 删除视频
     * @param id 主键id
     * @return ResponseEntity
     */
    public ResponseEntity delete(Long id) {
        super.removeById(id);
        return new ResponseEntity(HttpStatus.NO_CONTENT);
    }
}
```

这里我们编写了基本的增删改查，可以看到，我们仅仅需要继承ServiceImpl，并且填写两个泛型（Mapper和实体类）即可。之后我们便可以使用super.baseMapper调用我们的VideoMapper了。

ServiceImpl中内置了大量的方法，大家可以自行查看。

