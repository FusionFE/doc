## InputNumber 数字输入框

### 概述
使用鼠标或键盘输入一定范围的标准数值。

#### 使用
在模板中直接使用`v-input-number`标签即可。

#### API
Input props
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
max | 最大值 | Number | Infinity
min	| 最小值 | Number | -Infinity
value | 绑定的值，可使用 v-model 双向绑定 | Number | 1
size | 输入框尺寸，可选值为`large`、`small`、`default`或者不设置, 不设置默认`default` | String | -
disabled | 设置禁用状态 | Boolean | false
step | 每次改变的步伐，可以是小数 | Number | 1
Input events
事件名 | 说明 | 返回值
------------ | ------------- | -------------
on-change | 数值改变时的回调，返回当前值 | 当前值
