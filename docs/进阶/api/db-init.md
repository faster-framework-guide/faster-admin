# 数据库建立

在一切开始之前，我们首先需要设计数据库。

数据库我们应该遵循框架所要求的规范，必须包含以下字段及类型：

```
  `id` bigint(20) NOT NULL,
  `create_by` bigint(20) DEFAULT NULL COMMENT '创建人',
  `update_by` bigint(20) DEFAULT NULL COMMENT '最后更新人',
  `create_date` datetime NOT NULL COMMENT '创建时间',
  `update_date` datetime NOT NULL COMMENT '最后更新时间',
  `sort` int(11) NOT NULL DEFAULT '0' COMMENT '排序',
  `remark` varchar(1024) DEFAULT NULL COMMENT '备注',
  `deleted` tinyint(4) NOT NULL DEFAULT '0' COMMENT '是否删除（0.否 1.是）'
```


下面是video的sql示例：

```
CREATE TABLE `tb_video` (
  `id` bigint(20) NOT NULL,
  `category_id` bigint(20) DEFAULT NULL COMMENT '分类id',
  `name` varchar(128) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL COMMENT '标题',
  `url` varchar(1024) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL COMMENT 'url地址',
  `img` varchar(1024) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL COMMENT '封面图片',
  `content` longtext CHARACTER SET utf8mb4 COLLATE utf8mb4_bin COMMENT '内容',
  `time` int(11) DEFAULT NULL COMMENT '时长',
  `create_by` bigint(20) DEFAULT NULL COMMENT '创建人',
  `update_by` bigint(20) DEFAULT NULL COMMENT '最后更新人',
  `create_date` datetime NOT NULL COMMENT '创建时间',
  `update_date` datetime NOT NULL COMMENT '最后更新时间',
  `sort` int(11) NOT NULL DEFAULT '0' COMMENT '排序',
  `remark` varchar(1024) CHARACTER SET utf8mb4 COLLATE utf8mb4_bin DEFAULT NULL COMMENT '备注',
  `deleted` tinyint(4) NOT NULL DEFAULT '0' COMMENT '是否删除（0.,否 1.是）',
  `subject_id` bigint(20) DEFAULT NULL COMMENT '学科id',
  PRIMARY KEY (`id`) USING BTREE,
  KEY `idx_category_id` (`category_id`) USING BTREE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COMMENT='视频表';
```
