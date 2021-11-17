# 模块列表
----
Rocket(main)
- import(module)
- safemodule:检查roc文件是否有效，以及项目主体完整性。此模块必选。
- setmodule:对计算参数进行设置（calcmodule的前置模块）。
- loadmodule:加载，解析roc文件为实体。
- screenmodule:控制台输出模块。
- envmodule:环境模拟模块。
- calcmodule:计算模块。
# Rocket的组成
----
- Rocket_*参数集。
- head ——头部。
- body ——主体。
- end  ——尾部，以及发射平台（可选，若未填写则默认于[x,y,z+5]处发射）。

其中，**body**分为3个部分:
- left
- right
- center

您应该在定义body部分时考虑好```left```和```right```部分的重量，使其尽可能符合发射的要求。 
如果没有标注left或right，Load时会默认加载至center部分以平衡重量（V1.0版本支持）。
# roc文件编写说明
----
## Rocket_*
### Rocket_name
您Rocket的名称。
### Rocket_author
此Rocket的作者名。运行时会展示。
### Rocket_license
Rocket的安全证件，必须定义。但在进行定义时，请留意其现实中的安全性，不要全部定义为Safe。

目前可识别的有以下license:
- SafeV1  --安全类型
- SafeV2  --较安全的类型
- Danger  --危险类型

### Rocket_default
一些Default参数。定义这些参数有利于使用者的发射。

目前支持的参数:
- Rocket_defaultGround

-----
#### Rocket_defaultGround
Rocket于何种地面环境发射。

目前支持的地面环境：
- grass:一片草地。
- surface:空无的平面。
发射环境可以被使用者修改。
### Rocket_changeWarn
警告信息，在Rocket_default*被修改时输出于控制台。
## Load
Load命令用于解析数据。语法:
```
Load data_type
[line] [line_times]
data
```
*其中用中括号[]括起来的部分为可选参数。下同。

```line```可用于声明接下来有几行数据。
示例:
```
Load head
line 3
  *
 ***
*****
```
以上代码将加载一个三角形头部。