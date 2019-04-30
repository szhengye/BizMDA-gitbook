## index.yml

`index.yml`文件位于`template/{开发框架模板}`目录下，是约定所有要生成的目标文件及目录，如下所示：
```yaml
name: Jeecg-Boot快速开发框架
templates:
   #数据Entity实体类
 - file: Entity.java.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/entity/${className}.java
   #数据映射类
 - file: Mapper.java.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/mapper/${className}Mapper.java
   #数据映射配置文件
 - file: Mapper.xml.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/mapper/xml/${className}Mapper.xml
   #数据服务接口
 - file: Service.java.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/service/I${className}Service.java
   #数据服务实现类
 - file: ServiceImpl.java.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/service/impl/${className}ServiceImpl.java
   #数据控制类
 - file: Controller.java.vm
   model: data
   target: ${mda.sourcePath}/${mda.packagePath}/${module}/controller/${className}Controller.java
   #数据相关建表SQL文件
 - file: create-table.sql.vm
   model: data
   target: ${mda.resourcePath}/db/${module}/${name}.sql
   #数据列表VUE页面文件（带查询条件和分页，包括数据增、删、改，多条删除，以及EXCEL文件导入、导出，新增和编辑操作为弹出modal窗口）
 - file: QueryList1.vue.vm
   model: VIEW-QUERY-LIST1
   target: ${mda.resourcePath}/src/views/${module}/${className}.vue
   #数据列表的弹出modal窗口数据编辑VUE页面文件
 - file: QueryList1Modal.vue.vm
   model: VIEW-QUERY-LIST1
   target: ${mda.resourcePath}/src/views/${module}/modules/${className}Modal.vue
```

其中属性有：
* **file**：vm模板文件，都存放在`template/{开发框架模板}`目录下，即和`index.yml`文件同目录。
* **model**：分别匹配数据建模、视图建模、菜单建模、服务建模、字典建模，匹配规则如下：
  * **data**：为数据建模要生成的文件，根据`model/date`目录下的数据建模文件来生成文件。
  * **menu**：为菜单建模要生成的文件，根据`model/menu`目录下的菜单建模文件来生成文件。
  * **service**：为服务建模要生成的文件，根据`model/service`目录下的服务建模文件来生成文件。
  * **dictionary**：为字典建模要生成的文件，根据`model/dictionary`目录下的字贼胆建模文件来生成文件。
  * **大写字母属性**：为视图建模要生成的文件，根据`model/view`目录下的视图建模文件来生成文件，需要匹配视图建模文件中的model属性和这里的大写字母属性一致。
* **target**：文件生成的目标文件名和目标存放目录，这里是支持Velocity模板语法的，以"\$"开头的就是Velocity变量，其中“${mda.*}”变量中的值，和`model/mda.yml`中属性是一一对应的，具体参见[mda.yml应用参数文件](../ch1/MdaYml.md)。其它根据匹配的建模类型，会和对应的建模文件（数据建模、视图建模、菜单建模、服务建模、字典建模）会注入不同的属性值，具体属性值：
  * 数据建模：参见[数据建模data/*.yml](../ch1/Data.md)。
  * 视图建模：参见[视图建模view/*.yml](../ch1/View.dm)，以及各相关开发框架的view属性约定。
  * 菜单建模：参见菜单建模menu/*.yml。
  * 服务建模：参见服务建模service/*.yml。
  * 字典建模：参见字典建模dictionary/*.yml。

