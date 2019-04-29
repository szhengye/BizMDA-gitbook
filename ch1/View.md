## 视图建模文件

视图建模文件为`model/view/*.yml`，主要参数为：
* name：视图名，生成的视图文件以此名称命名。
* label：视图的标签描述
* module：模块名，针对一个项目会有多个模块，每个模块会员有多个视图，视图和数据表一样，也是挂在模块项下的。
* model：视图展现模板，针对不同的视图展现风格，会有不同的视图展现模块。
* components：视图中的组件，一个视图是由一个到多个组件来组成，每个组件绑定一个数据表或一个服务。
  * type：组件类型，一般用来标识同一个视图中不同组件的类型，具体的组件类型名称，由视图模块开发方约定。
  * dataName：组件绑定的数据表外，数据表是在`model/data`中进行定义。
  * view：组件的附加属性，具体的属性和用法，由视图模块开发方约定。
  * fields：组件项下的域列表。
    * name：域名，参见组件绑定数据表项下中的域列表。
    * view：域的附加属性，具体的属性和用法，由视图模块开发方约定。

------

数据建模文件样例（`model/view/customer-list.yml`）：

```yaml
#视图名称
name: customer-list
#标签
label: 客户列表
#所属模块
module: crm
#视图展现模块
model: VIEW-QUERY-LIST1
#查询条件域列表
components:
  #视图类型：QUERY、MASTER、DETAIL
  - type: QUERY
    #相关数据表
    dataName: customer
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
    #视图类型：QUERY、MASTER、DETAIL
  - type: LIST
    #相关数据表
    dataName: customer
    #视图扩展属性
    view:
    fields:
      #域名
      - name: cust_no
      #视图扩展属性
        view:
        #提示信息
          placeholder: 输入客户编号
      - name: cust_name
        view:
          #提示信息
          placeholder: 输入客户名称
      - name: cust_region
      - name: cust_address
      - name: cust_registered_capital
    actions:
    #视图类型：QUERY、MASTER、DETAIL
  - type: MODAL
    #相关数据表
    dataName: customer
    #视图扩展属性
    view:
    fields:
      #域名
      - name: cust_no
      - name: cust_name
      - name: cust_region
      - name: cust_address
      - name: cust_registered_capital
    actions:
```
