## Notice 通知提醒

### 概述
在界面右侧显示可关闭的全局通知，常用于以下场景：
* 通知内容带有描述信息
* 系统主动推送

#### API
通过直接调用以下方法来使用组件：
* `this.$notice.open(config)`
* `this.$notice.info(config)`
* `this.$notice.success(config)`
* `this.$notice.warning(config)`
* `this.$notice.error(config)`

以上方法隐式地创建及维护Vue组件。参数 config 为对象，具体说明如下：

属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
title | 通知提醒的标题 | String | -
msg | 通知提醒的内容，为空或不填时，自动应用仅标题模式下的样式 | String | -
link | 自定义动作的入口，位置在 `msg` 后面 | Object | null
duration | 自动关闭的延时，单位毫秒，不关闭可以写 0 | Number | 3000
onClose | 关闭时的回调 | Function | null

其中`link`包含`label`和`action`两个属性：
* `label`为动作链接的文本，类型为`String`
* `action`为点击动作链接的回调方法，类型为`Function`

示例代码如下：
``` javascript
// 保存失败后重新保存
this.$notice.error({
  title: '保存失败',
  msg: '保存 XXX 时响应超时',
  link: {
    label: '重新保存',
    action: (closeNotice) => {
      this.saveData().then((data) => {
        if (data.success) {
          // do something
          closeNotice()
        } else {
          // do something else
        }
      })
    }
  }
})
```
``` javascript
// 带跳转详情的连接
this.$notice.success({
  title: '上传成功',
  msg: 'XXX 已成功上传到服务器',
  link: {
    label: '点击查看详情',
    action: (closeNotice) => {
      // vue 1.0
      this.$router.go({
        name: 'details',
        params: {
          id: this.upLoadItemId
        }
      })
      closeNotice()

      // vue 2.0
      this.$router.push({
        name: 'details',
        params: {
          id: this.upLoadItemId
        }
      })
      closeNotice()
    }
  }
})
```

另外，提示组件列表距离顶端的距离，在全局样式文件`variables.mixin.less`中由`@app-notice-top`定义；提示列表的排序默认是从上到下的，如果想要改为从下往上，需要在`main.js`中初始化时，传入参数`reverse: true`，示例如下：
``` javascript
import VueNotice from './plugins/vueNotice/vueNotice'

Vue.use(VueNotice, {
  reverse: true,
  duration: 4500,
  transition: 0
})
```
以上代码除了配置了列表的顺序外，还修改了自动关闭的延迟时间`duration`以及关闭动画的过度时间`transition`，例子中的 0 毫秒表示禁用动画效果。