## Transfer 穿梭框

### 概述
双栏穿梭选择框，常用于将多个项目从一边移动到另一边。

#### 使用
在模板中直接使用`transfer`标签即可。

#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
keyName | 每个数据项中作为索引的键，默认去`key`值作为索引 | String | key
v-model | 目标列表，用来存放转移后的数据项 | Array | []
source | 源列表，包含每个数据项 | Array | []
renderFormater | 每个数据项的渲染函数 | Function | 默认显示`label`
filterable | 过滤器开关，`true`开启，`false`关闭 | Boolean | true
filterMethod | 过滤算法 | Function | 默认在`label`中检索

#### 事件
事件名 | 说明 | 返回值
------------ | ------------- | -------------
on-change | 选项在两栏之间转移时触发该事件 | v-model绑定的值

## 示例