# Mapper

实体创建完成后，我们需要创建Mybatis的接口，以保证可以操作数据库。

由于我们使用Mybatis-plus，所以我们仅需要继承BaseMapper即可。

路径：/src/main/java/你的根包/modules/你的业务名/mapper
文件：业务名Mapper.java

下面是一个例子：

```
package com.admin.modules.video.mapper;

import com.baomidou.mybatisplus.core.mapper.BaseMapper;
import com.admin.modules.video.entity.Video;

/**
 * @author faster-builder
 * 视频 Mapper
 */
public interface VideoMapper extends BaseMapper<Video> {
}
```

其中BaseMapper的泛型填写我们的实体类。



