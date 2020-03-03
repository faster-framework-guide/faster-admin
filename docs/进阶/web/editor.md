# 富文本

我们使用braft-editor作为富文本编辑器。

引入：

```
import Editor from '@/common/components/BraftEditor';
```

使用：

```
<FixedRow editor>
    <Form.Item label="介绍">
            {
              getFieldDecorator("content", { rules: [{ required: true }] })(<Editor />)
            }
    </Form.Item>
</FixedRow>
```

