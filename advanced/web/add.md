# 添加页


添加页一般由表格页的弹框打开，表格页面的写法如下：

```
<Button type="primary" icon="plus" onClick={() => this.refs.addModal.show()}>添加</Button>
<ModalInfo title='添加视频' ref="addModal" {...this.refs}>
    <VideoAdd />
</ModalInfo>
```

两个步骤：
1. 定义ModalInfo，要打开哪个页面，如VideoAdd
2. 通过onClick事件，打开ModalInfo。this.refs.addModal.show()


添加页面的内容一般是表单，一个基本的表单示例如下：

```
import React, { Component } from 'react';
import { Input, Form, message } from 'antd';
import FixedRow from '@/common/components/FixedRow';
import request from '@/common/utils/request';

class VideoAdd extends Component {
  constructor(props) {
    super(props)
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
export default Form.create()(VideoAdd);
```