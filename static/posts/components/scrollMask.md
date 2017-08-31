## ScrollMask 滚动遮罩

### 概述
该组件是一个 scroll 容器，会在滚动方向的两侧生成渐隐的效果。

#### 使用
在模板中直接使用`scroll-mask`标签即可，该组件使用`slot`的方式分发内容。

#### 属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
scroll-direction | 滚动方向，纵向为`true`，横向为`false` | Boolean | true
container-class | 滚动容器`class`列表，自定义的容器样式需要定义在`class`中，并将`class`加入列表 | Array | []
max-length | 最大长度，字符串类型，需要自带单位，例如`10em`、`45px`等 | String | 5em
