## 字典建模文件

数据建模文件为`model/dictionary/**/*.yml`，其中中间的`/**/`目录，为模块名，文件名则对应字典名称，模块名+字典名在调用时会引用，主要参数为：

| 配置项      | 配置说明                               |
| ----------- | -------------------------------------- |
| text        | 字典中文描述                           |
| items       | 可容纳多条item项目，每条对应一条字典项 |
| items.text  | 字典项描述                             |
| items.value | 字典项的值                             |


字典建模文件样例（`model/dictionary/sex.yml`）：

```yaml
#字典标签
text: 性别
#条目列表
items:
   #条目标签
 - text: 男
   #条目值
   value: M
 - text: 女
   value: F
```
