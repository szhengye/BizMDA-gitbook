## VM模板文件

VM模板文件是支持Velocity模板语法的，以"\$"开头的就是Velocity变量，其中“${mda.*}”变量中的值，和`model/mda.yml`中属性是一一对应的，具体参见[mda.yml应用参数文件](../ch1/MdaYml.md)。其它根据匹配的建模类型，会和对应的建模文件（数据建模、视图建模、菜单建模、服务建模、字典建模）会注入不同的属性值，具体属性值：
* 数据建模：参见[数据建模data/*.yml](../ch1/Data.md)。
* 视图建模：参见[视图建模view/*.yml](../ch1/View.dm)，以及各相关开发框架的view属性约定。
* 菜单建模：参见菜单建模menu/*.yml。
* 服务建模：参见服务建模service/*.yml。
* 字典建模：参见字典建模dictionary/*.yml。
