## 应用参数文件

应用参数文件为`model/mda.yml`，主要参数为：
* author：开发人员名，会标明在各生成文件注释中。
* email：同上，为开发人员邮箱。
* version：版本号。
* packageName：生成Java代码的包名。
* sourcePath：指明代码生成时的输出目录。
* resourcePath：指明资源文件生成时的输出目录。
* template：指明采用哪一套开发框架模板来生成代码和资源文件。

------

`mda.yml`样例：

```yaml
#代码作者名
author: Steven
#代码作者邮箱
email: steven@bizmda.com
#版本号
version: V1.0
#生成代码所属java包名
packageName: com.bizmda
#生成代码文件所在目录
sourcePath: tmp/src
#生成资源文件所在目录
resourcePath: tmp/resource
#生成代码所用的模板名
template: Jeecg-Boot
```
