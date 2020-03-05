# 列表页面

列表页的一般组成如下图所示：

![](../../../_media/web-list1.png)

一个基本的表格示例如下：

```
import React, { Component } from 'react';
import { Input, Button, message, Modal } from 'antd';
import { GridContent } from '@ant-design/pro-layout';
import ModalInfo from '@/common/components/Modal';
import TableList, { Search, Table, Action } from '@/common/components/TableList';
import request from '@/common/utils/request'
import Permission from '@/common/components/Permission';

import VideoAdd from './VideoAdd';
import VideoEdit from './VideoEdit';

export default class VideoList extends Component {

  constructor(props) {
    super(props);
    // 默认筛选参数，key与下方筛选条件内的name相对应
    this.defaultParam = {
    }
  }
  /**
   * 渲染操作列
   * text: 当前行的值
   * record: 当前行数据
   * index: 行索引
   */
  renderColAction = (text, record, index) => {
    return (
      <>
        <Permission authority="video:modify">
          <a onClick={() => this.refs.editModal.show(record)}>修改</a>
        </Permission>
        <Permission authority="video:delete">
          <a onClick={() => this.delete(record)}>删除</a>
        </Permission>
      </>
    );
  }
  /**
   * 删除
   */
  delete = (record) => {
    const tableList = this.refs.tableList;
    const selectRecrods = tableList.currentSelectRows(record);
    if (selectRecrods.length == 0) {
      message.error('请选择至少一条记录！');
      return;
    }
    Modal.confirm({
      title: '删除',
      okText: "确认",
      cancelText: "取消",
      centered: true,
      content: '删除操作不可恢复，确认删除？',
      onOk() {
        return new Promise((resolve, reject) => {
          request.delete("/video/delete", { data: selectRecrods.map(item => item.id) } ).then(res => {
            resolve();
            tableList.reload();
          }).catch(() => reject());
        });
      }
    });
  }
  render() {
    return (
      <GridContent>
        <TableList ref='tableList'>
          <Search>
            <Input label='分类id' name='categoryId' />
            <Input label='标题' name='name' />
            <Input label='url地址' name='url' />
            <Input label='封面图片' name='img' />
            <Input label='内容' name='content' />
            <Input label='时长' name='time' />
            <Input label='学科id' name='subjectId' />
          </Search>
          <Action>
            <Permission authority="video:add">
              <Button type="primary" icon="plus" onClick={() => this.refs.addModal.show()}>添加</Button>
            </Permission>
            <Permission authority="video:delete">
              <Button type="primary" icon="delete" onClick={() => this.delete()}>删除</Button>
            </Permission>
          </Action>
          <Table url='/video' defaultParam={this.defaultParam}>
            <Table.Column title="分类id" dataIndex="categoryId" />
            <Table.Column title="标题" dataIndex="name" />
            <Table.Column title="url地址" dataIndex="url" />
            <Table.Column title="封面图片" dataIndex="img" />
            <Table.Column title="内容" dataIndex="content" />
            <Table.Column title="时长" dataIndex="time" />
            <Table.Column title="学科id" dataIndex="subjectId" />
            <Table.Action render={this.renderColAction}></Table.Action>
          </Table>
        </TableList >
        <ModalInfo title='添加视频' ref="addModal" {...this.refs}>
          <VideoAdd />
        </ModalInfo>
        <ModalInfo title='编辑视频' ref="editModal" {...this.refs}>
          <VideoEdit />
        </ModalInfo>
      </GridContent >
    );
  }
}
```