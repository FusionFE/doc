## Radio 单选框

### 概述
基础组件，主要用于一组可选项的单项选择。

#### 使用
在模板中直接使用`v-radio`标签即可，该组件使用`slot`的方式分发内容，如`icon`和按钮`label`。

#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
type | 单选框类型，包括`defalut`、`button` | String | defalut
size | 单选框大小，包括`large`、`default`、`small`、`mini`，只在按钮（`button`）类型下生效 | String | default
shape | 单选框形状，包括`default`、`circle`，只在按钮（`button`）类型下生效 | String | default
v-model | 为单选框绑定变量，用于实时获取和更新单选框组被选中的值 | - | -
name | 单选框的组名，同一组单选框需要传入同一个名字 | String | -
value | 单选框的值，被选中时，`v-model`绑定的变量将被赋予该值 | String、Number、Boolean | -
disabled | 单选框是否禁用，`true`为禁用 | Boolean | false

## RadioGroup 单选框组

### 概述
单选框组件的包装层，用来为按钮（`button`）类型的单选框分组。

#### 使用
在模板中直接使用`v-radio-group`标签即可，该组件使用`slot`的方式分发按钮组件。

#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
vertical | 是否垂直，`true`表示垂直方向 | Boolean | false

## 示例