## 视图建模文件

视图建模文件为`model/view/**/*.yml`，其中中间的`/**/`目录，为模块层次，文件名则对应视图名，针对不同的视图模块，参数不尽相同，具体请参见模块的建模参数描述，其中主要的共性参数为：
| 配置项      | 配置说明                               |
| ----------- | -------------------------------------- |
|label|视图的标签描述|
|model|视图展现模板，针对不同的视图展现风格，会有不同的视图展现模块。|
|view |视图的附加属性，具体的属性和用法，由视图模块开发方约定。 |
|components |视图中的组件，一个视图是由一个到多个组件来组成，每个组件绑定一个数据表或一个服务。 |
|components.type |组件类型，一般用来标识同一个视图中不同组件的类型，具体的组件类型名称，由视图模块开发方约定。 |
|components.tableName |组件绑定的数据表，数据表是在`model/data`中进行定义。 |
|components.view |组件的附加属性，具体的属性和用法，由视图模块开发方约定。 |
|components.fields |组件项下的域列表 |
|components.fields.name |域名，参见组件绑定数据表项下中的域列表 |
|components.fields.view |域的附加属性，具体的属性和用法，由视图模块开发方约定 |
|components.actions |组件项下的动作列表 |
|components.actions.type |动作类型 |
|components.actions.label |动作标签描述 |
|components.actions.icon |动作图标 |

------

数据建模文件样例（`model/view/crm/customer-list-1.yml`）：

```yaml
#标签
label: 客户列表
#视图展现模块
model: LIST-1
#查询条件域列表
components:
  #视图类型：查询条件组件
  - type: QUERY
    #相关数据表
    tableName: customer
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
    #相关数据表
    tableName: customer
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
