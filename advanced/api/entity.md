# 实体类

当我们建立好数据库后，我们便需要建立与之对应的数据库实体。

路径：/src/main/java/你的根包/modules/你的业务名/entity
文件：业务名.java

以下是video的示例：

```
package com.admin.modules.video.entity;

import cn.org.faster.framework.mybatis.entity.BaseEntity;
import lombok.Data;
import com.baomidou.mybatisplus.annotation.TableName;
import lombok.EqualsAndHashCode;

/**
 * @author faster-builder
 * 视频 实体
 */
@Data
@EqualsAndHashCode(callSuper = true)
@TableName("tb_video")
public class Video extends BaseEntity{
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


解释其中的几个关键点：

1. @Data是Lombok的注解，可以省略我们的setter、getter方法，程序会在编译期自动生成setter、getter方法，但是如果我们在idea中直接允许时，需要开启lombok插件（具体请看环境配置一章），如果是使用maven打包则不需要配置插件。
2. @EqualsAndHashCode(callSuper = true)同样是Lombok注解，它可以生成默认的equals和hashcode方法，默认情况下@Data会包含该注解的功能，但是由于我们继承其他类，所以需要重新设置callSuper = true属性，其意义在于在生成前会先调用父类的计算方法。
3. @TableName("tb_video")是mybatis-plus的注解，表示该实体类对应的表名。
4. BaseEntity是我们定义的基本类，里面包含了我们的公共字段。
5. 类中各个属性的定义是数据库字段转驼峰后的命名，如subject_id转为驼峰后是subjectId。