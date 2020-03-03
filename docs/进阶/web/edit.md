# 编辑页

编辑页与添加页的内容基本一致，唯一的区别在于需要在初始化页面的时候需要根据当前id获取数据，并且加载到页面上。

仅需要在添加页代码的基础上，增加以下代码，并且修改页面名称即可：

```
constructor(props) {
    super(props)
    request.get('/video/' + this.props.currentRecord.id).then(res => {
      this.props.form.setFieldsValue(res);
    });
  }
```

全部代码如下：

```
import React, { Component } from 'react';
import { Input, Form, message } from 'antd';
import FixedRow from '@/common/components/FixedRow';
import request from '@/common/utils/request';

class VideoEdit extends Component {
  constructor(props) {
    super(props)
    request.get('/video/' + this.props.currentRecord.id).then(res => {
      this.props.form.setFieldsValue(res);
    });
  }

  onOk(modal) {
    this.props.form.validateFields((err, values) => {
      if (!!err) {
        return;
      };
      request.post('/video', { data: values }).then(res => {
        //提交成功
        message.success('保存成功');
        modal.hideAndRefresh();
      });

    });
  }
  render() {
    const { getFieldDecorator } = this.props.form;
    return (
      <Form>
        <FixedRow>
          <Form.Item label="分类id">
            {
              getFieldDecorator("categoryId", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="标题">
            {
              getFieldDecorator("name", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="url地址">
            {
              getFieldDecorator("url", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="封面图片">
            {
              getFieldDecorator("img", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="内容">
            {
              getFieldDecorator("content", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="时长">
            {
              getFieldDecorator("time", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
        <FixedRow>
          <Form.Item label="学科id">
            {
              getFieldDecorator("subjectId", {  })(<Input />)
            }
          </Form.Item>
        </FixedRow>
      </Form >
    );
  }
}
export default Form.create()(VideoEdit);

```