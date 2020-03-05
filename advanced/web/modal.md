# 弹框

弹框一般用于列表页的操作区按钮，点击弹出添加、编辑、二级页面等功能的使用。

一般流程如下：


引入：

```
import ModalInfo from '@/common/components/Modal';
```

定义：
```
<ModalInfo title='编辑视频' ref="editModal" {...this.refs}>
    <VideoEdit /> 
</ModalInfo>
```

其中VideoEdit为我们要弹出的页面内容页，需要我们自己编写。


调用：

```
onClick={() => this.refs.addModal.show()}
```