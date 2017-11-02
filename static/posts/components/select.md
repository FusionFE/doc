## Select 选择器

### 概述
使用模拟的增强下拉选择器来代替浏览器原生的选择器。
选择器支持单选、多选、搜索操作。

#### 使用
在模板中直接使用`v-select`标签即可。

#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
value | 指定选中项目的 value 值，可以使用 v-model 双向绑定数据。单选时只接受 String 或 Number，多选时只接受 Array | String | Number | Array | 空
multiple | 是否支持多选 | Boolean | false
disabled | 是否禁用 | Boolean | false
placeholder | 选择框默认文字 | String | 请选择
filterable | 是否支持搜索 | Boolean | false
placement | 弹窗的展开方向，可选值为 down 和 up | String | down
optionDisabled | 禁用的选项，是value值 | Array | 空
#### API