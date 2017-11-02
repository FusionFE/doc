## Confirm 确认对话框

### 概述
为用户提供 2 选 1 的交互对话框，包含标题`title`，内容`msg`，确认按钮（primary类型）和取消按钮（text类型），每个按钮都可以绑定对应的处理方法。

#### API
通过直接调用以下方法来使用组件：
* `this.$confirm.show(config)`
* `this.$confirm.hideAll()`

调用`show`方法显示确认对话框，每次调用都会在对话框队列中添加一个对话框实例，当前展示最先进入队列的对话框。此外，`show`方法返回一个关闭函数，可以调用该关闭函数来关闭对应的对话框，（注意：以这种方式关闭并不会触发绑定的回调）。当对话框队列为空时，页面将不再显示对话框。`show`方法的参数 config 为对象，具体说明如下：

#### Config属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
backdrop | 是否显示背景遮罩层，默认显示 | Boolean | true
color | 遮罩层的颜色 | String | #000000
opacity | 遮罩层的透明度 | Number | 0.2
title | 对话框标题 | String | ''
msg | 对话框内容 | String | ''
confirmText | 确认按钮文本，对于国际化需求，可在启用插件时注入默认的国际化文本 | String | 'OK'
cancelText | 取消按钮文本，对于国际化需求，可在启用插件时注入默认的国际化文本 | String | 'Cancel'
onConfirm | 确认的回调方法 | Function | () => {}
onCancel | 取消的回调方法 | Function | () => {}

调用`hideAll`方法，一次清空遮罩队列。

该组件默认在`main.js`中进行注册（注意：由于内部使用了`v-button`组件，所以请在按钮组件注册完成后进行该插件的注册；另外，如果`v-button`组件中调用了`vuex`等插件，则需要在config中传入store对象），支持全局修改默对话框配置，可选配置项包括：`opacity`、`backdrop`、`color`、`confirmText`、`cancelText`、`store`，示例代码如下：
``` javascript
import VueI18n from 'vue-i18n'
import VueConfirm from './plugins/vueConfirm/VueConfirm'

import store from './vuex/store'
import i18nMessage from './lib/i18n'

const i18n = new VueI18n({
  locale: 'zh-CN',
  silentTranslationWarn: true,
  missing: (locale, key, vm) => {
    return key
  },
  messages: i18nMessage
})

Vue.use(VueConfirm, {
  color: '#FFFFFF',
  opacity: 0.7,
  confirmText: i18n.t('text.confirm'),
  cancelText: i18n.t('text.cancel'),
  store
})
```

## 示例

以下为 vue 组件中的片段代码（点击下方按钮，查看运行效果）：
``` html
<div>
  <v-button @click.native="showConfirm(false)">打开confirm（无背板）</v-button>
  <v-button @click.native="showConfirm(true)">打开confirm</v-button>
  <v-button @click.native="hideAllConfirm">关闭所有confirm</v-button>
</div>
```
``` javascript
methods: {
  showConfirm (backdrop) {
    var opt = {
      backdrop: backdrop,
      title: (backdrop ? '有' : '无') + '背板的确认框，标题要长点，这样才能测出问题哦',
      msg: '需要用户确认的信息，二选一，不能取消，不能取消，不能取消，重要的事情说三遍。',
      onConfirm () {
        this.$message.success('用户确认了')
      },
      onCancel () {
        this.$message.error('用户拒绝了')
      },
      confirmText: '欣然接受',
      cancelText: '残忍拒绝'
    }
    this.$confirm.show(opt)
  },
  hideAllConfirm () {
    this.$confirm.hideAll()
  }
}
```