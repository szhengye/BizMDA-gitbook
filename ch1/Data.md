## 数据建模文件

数据建模文件为`model/data/*.yml`，主要参数为：
* name：数据表名，为数据库中的物理表表名
* label：数据表的标签描述
* module：模块名，针对一个项目会有多个模块，每个模块会员有多张数据表，数据表是挂在模块项下的。
* primaryKey：主键名，是为后面`fields`中的一个域。
* primaryKeyType：主键生成的规则（MANUAL-手工输入，为缺省模式；UUID-32位以UUID模式自动生成；AUTO_INCREMENT-数据库的自增类型，为整数）。
* hasStatus：标识是否物理删除，如为TRUE，则会自动生成mda_status域（0-正常 1-删除 2-停用）。
* hasCreateUpdate：标识是否跟踪创建和更新，会自动生成create_by、create_date、update_by、update_date，分别对应创建者、创建时间、最后修改者、最后修改时间。
* fields：是当前数据表项下的各域定义。
  * name：域名。
  * label：域标签名称。
  * type：域类型，数据类型：int,float,decimal,date,datetime,boolean,varchar(?),char(?),blob，file
  * showType：输入类型：text,textarea,checkbox,radiobox,select,lookup
  * dictName：相关字典名，具体字典在`model/dictionary`中定义。
  * isNull：是否允许为空。

------

数据建模文件样例（`model/data/customer.yml`）：

```yaml
#表名
name: customer
#标签
label: 客户
#所属模块
module: crm
#主键
primaryKey: cust_no
#主键生成规则（MANUAL-手工输入(缺省) UUID-UUID AUTO_INCREMENT-自增）
primaryKeyType: UUID
#是否物理删除,会自动生成mda_status域（0正常 1删除 2停用）
hasStatus: false
#是否跟踪创建和更新，会自动生成create_by,create_date,update_by,update_date
hasCreateUpdate: false
#域列表
fields:
   #域名
 - name: cust_no
   #域标签
   label: 客户编号
   #数据类型：int,float,decimal(19,2)-money,date,datetime,tinyint-boolean,varchar(100),char(10),blob
   type: char(32)
   #输入类型：text,textarea,checkbox,radiobox,select
   inputType: text
   #相关字典名
   dictName:
   #允许为空
   isNull: false
 - name: cust_name
   label: 客户名称
   type: varchar(20)
   inputType: text
   isNull: false
 - name: cust_region
   #域标签
   label: 所在地区
   #数据类型：int,float,decimal(19,2)-money,date,datetime,tinyint-boolean,varchar(100),char(10),blob
   type: varchar(5)
   #输入类型：text,textarea,checkbox,radiobox,select
   inputType: select
   #相关字典名
   dictName: region
   #允许为空
   isNull: true
 - name: cust_address
   #域标签
   label: 地址
   #数据类型：int,float,decimal(19,2)-money,timestamp,tinyint-boolean,varchar(100),char(10),blob
   type: varchar(100)
   #输入类型：text,textarea,checkbox,radiobox,select
   inputType: text
 - name: cust_registered_capital
   #域标签
   label: 注册资金
   #数据类型：int,float,decimal(19,2)-money,timestamp,tinyint-boolean,varchar(100),char(10),blob
   type: decimal(19,2)
   #输入类型：text,textarea,checkbox,radiobox,select
   inputType: text
   #允许为空
   isNull: true
```
