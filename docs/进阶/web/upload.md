# 文件上传

## 上传图片

引入：

```
import UploadImg from '@/common/components/UploadImg'
```

在表单中使用：

```
<FixedRow upload>
    <Form.Item label="上传图片">
    {getFieldDecorator('imgs', { rules: [] })(
              <UploadImg />
    )}
    </Form.Item>
</FixedRow>
```

效果：

![](../../../_media/upload-img1.png)

![](../../../_media/upload-img2.png)

可以指定maxFile来限定上传的文件数量。

```
<FixedRow upload>
    <Form.Item label="上传图片">
    {getFieldDecorator('imgs', { rules: [] })(
              <UploadImg maxFile={2}/>
    )}
    </Form.Item>
</FixedRow>
```