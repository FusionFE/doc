## Message 全局提示

### 概述
轻量级的信息反馈组件，在顶部居中显示，并可以自动消失。有多种不同的提示状态可选择。

#### API
通过直接调用以下方法来使用组件：
* `this.$message.info(config)`
* `this.$message.success(config)`
* `this.$message.warning(config)`
* `this.$message.error(config)`
* `this.$message.loading(config)`

以上方法隐式的创建及维护 Vue 组件。参数 config 可以是字符串或对象，当为字符串时，直接显示内容，当为对象时，具体说明如下：

属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
msg | 提示内容 | String | -
duration | 自动关闭的延时，单位毫秒，不关闭可以写 0 | Number | 1500
onClose | 关闭时的回调 | Function | null

另外，提示组件距离顶端的距离，在全局样式文件`variables.mixin.less`中由`@app-message-top`定义。