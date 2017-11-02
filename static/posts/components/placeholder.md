## Placeholder 占位反馈

### 概述
信息反馈组件，居中显示，有`loading`、`error`、`noData`几种不同的提示类型可选择。

#### 使用
在模板中直接使用`placeholder`标签即可，该组件使用slot的方式分发内容，如示例中button。


#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
type | 提示类型，可选值为 `loading`、`error`、`noData`| String | loading
msg | 提示文本 | String | loading：正在加载数据；noData：未查询到匹配数据；error：加载失败

## 示例