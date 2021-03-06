### VIEW模板:LIST-1
模板**LIST-1**主要是生成主页面为带查询条件和分页的数据列表，支持数据增、删、改、以及多条删除、EXCEL文件导入、导出。

配置文件如下例（customer-list-1.yml）：

```yaml
#标签
label: 客户列表
#视图展现模块
model: LIST-1
#相关数据表
tableName: customer
#查询条件域列表
components:
  #视图类型：查询条件组件
  - type: QUERY
    #视图扩展属性
    view:
    fields:
      #域名
    - name: cust_no
      #视图扩展属性
      view:
        #提示信息
        placeholder: 输入客户编号
        #查询条件类型: EQ GE LE LIKE BETWEEN
        queryType: EQ
        #跨度
        span: 6
      #域名
    - name: cust_name
      view:
        #提示信息
        placeholder: 输入客户名称
        #查询条件类型: EQ GE LE LIKE BETWEEN
        queryType: EQ
        #跨度
        span: 6
    actions:
    #视图类型：数据列表组件
  - type: LIST
    #视图扩展属性
    view:
      modalView: /crm/CustomerFormModal1
    fields:
      #域名
      - name: cust_no
      - name: cust_name
      - name: cust_region
      - name: cust_address
      - name: cust_registered_capital
    #按钮动作
    actions:
      #动作类型
      - type: LIST-OPEN-VIEW
        label: 查看
        icon: read
        params:
          view: /crm/CustomerForm1
          query: "{mda_id: record.custNo}"
      - type: LIST-DO-SERVICE
        label: 删除服务
        icon: delete
        params:
          method: delete
          url: /crm/customer/delete
          data: "{id: record.custNo}"
          confirm: true
      - type: LIST-DELETE
        label: 删除
        icon: delete
      - type: LIST-EDIT-WITH-MODAL
      - type: ADD-WITH-MODAL
      - type: BATCH-DELETE
      - type: OPEN-VIEW
        label: 打开视图
        icon: folder-open"
        params:
          view: /crm/CustomerForm1
          confirm: true
      - type: DO-SERVICE
        label: 执行服务
        icon: interation
        params:
          method: delete
          url: /crm/customer/delete
      - type: EXPORT-EXCEL
        label: 导出
        icon: download
      - type: IMPORT-EXCEL
        label: 导入
        icon: import
```
在视图中涉及到QUERY、LIST共2个component（组件），效果如下：

![image](pic/list-1.jpg)
