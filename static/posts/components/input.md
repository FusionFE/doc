## Input 输入框

### 概述
基本表单组件，支持 input 和 textarea，并在原生控件基础上进行了功能扩展，可以组合使用。

#### 使用
在模板中直接使用`v-input`标签即可。

#### API
Input props
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
type | 输入框类型，可选值为 `text`、`password` 或 `textarea` | String | text
value | 绑定的值，可使用 v-model 双向绑定 | String | Number | -
size | 输入框尺寸，可选值为`large`、`small`、`default`或者不设置 | -
placeholder	| 占位文本 | String | -
disabled | 设置输入框为禁用状态 | Boolean | false
readonly | 设置输入框为只读 | Boolean | false
maxlength | 最大输入长度 | Number | -
prefixIcon | 带有前缀图标的input | String | -
suffixIcon | 带有后缀图标的input | String | -
rows | 文本域默认行数，仅在 textarea 类型下有效 | Number | 2
autosize | 自适应内容高度，仅在 textarea 类型下有效，可传入对象，如 { minRows: 2, maxRows: 6 } | Boolean | Object | false
number | 将用户的输入转换为 Number 类型 | Boolean | false
autocomplete | 原生的自动完成功能，可选值为 off 和 on | String | off
Input events
事件名 | 说明 | 返回值
------------ | ------------- | -------------
on-enter | 按下回车键时触发 | -
on-change | 数据改变时触发 | -
on-keyup | 原生的 keyup 事件 | -
on-keydown	| 原生的 keydown 事件 | -
on-prefix-click| 设置 icprefixIconon 属性后，点击图标时触发 | -
on-suffix-click| 设置 suffixIcon 属性后，点击图标时触发 | -
on-focus | 输入框聚焦时触发 | -
on-blur | 输入框失去焦点时触发 | -
Input slot 
名称 | 说明
------------ | -------------
prepend | 前置内容，仅在 text 类型下有效
append | 后置内容，仅在 text 类型下有效