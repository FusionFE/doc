## PageMask 页面遮罩

### 概述
用于遮盖页面（或者页面的一部分），阻止用户进行交互操作。常用于以下场景：
* 任务阻塞UI前，弹出以阻止用户交互
* 业务需要完成某些特定步骤才能与页面其他元素交互

#### API
通过直接调用以下方法来使用组件：
* `this.$mask.show(config)`
* `this.$mask.hideAll()`
* `this.$mask.play()`
* `this.$mask.pause()`

调用`show`方法显示页面遮罩，每次调用都会在遮罩队列中添加一个遮罩实例。该方法返回一个关闭函数，调用该返回函数来关闭对应的遮罩。当遮罩队列为空时，页面不再显示遮罩。`show`方法的参数 config 为对象，具体说明如下：

#### Config属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
color | 遮罩层的颜色 | String | #000000
opacity | 遮罩层的透明度 | Number | 0.2
showLoading | 是否显示载入状态提示，默认显示 | Boolean | true
loadingMsg | 载入状态的提示文本 | String | -
top | 与浏览器窗口上边缘的距离（带单位，遵循CSS规则） | String | 0px
bottom | 与浏览器窗口下边缘的距离（带单位，遵循CSS规则） | String | 0px
left | 与浏览器窗口左边缘的距离（带单位，遵循CSS规则） | String | 0px
right | 与浏览器窗口右边缘的距离（带单位，遵循CSS规则） | String | 0px

调用`hideAll`方法，一次清空遮罩队列。
调用`play`方法，播放当前遮罩的“载入中”动画。
调用`pause`方法，暂停当前遮罩的“载入中”动画。

该组件默认在`main.js`中进行注册，支持全局修改默认遮罩配置，配置项同上方`config`，示例代码如下：
``` javascript
import VuePageMask from './plugins/vuePageMask/VuePageMask'

Vue.use(VuePageMask, {
  color: '#FFFFFF',
  opacity: 0.7,
  loadingMsg: '处理中…'
})
```

## 示例

以下为 vue 组件中的片段代码（点击下方按钮，查看运行效果）：
``` html
<div>
  <v-button @click.native="showMask">显示Mask</v-button>
</div>
```
``` javascript
data () {
  return {
    close () {}
  }
},
methods: {
  showMask () {
    this.close = this.$mask.show({
      loadingMsg: '报表生成中…'
    })
    setTimeout(this.showNotice, 5000)
  },
  showNotice () {
    this.$mask.pause()
    this.$notice.error({
      title: '生成失败',
      msg: '内存不足，报表生成失败，',
      link: {
        label: '关闭任务',
        action: (closeNotice) => {
          this.close()
          closeNotice()
        }
      },
      duration: 0,
      onClose: this.close
    })
  }
}
```