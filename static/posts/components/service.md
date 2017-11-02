## Service 服务器通信

### 概述
该插件提供一种容易的方式与 RESTful APIs 配合，内部调用 [vue-resource](https://github.com/vuejs/vue-resource)，各个请求方法均返回一个`Promise`对象。

#### API
通过直接调用以下方法来直接与服务器通讯：
* `this.$service.get(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.head(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.delete(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.jsonp(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.post(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.put(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.patch(context, url, param, emulateJSON, timeout, requestKey)`
* `this.$service.static(context, url, param, emulateJSON, timeout, requestKey)`

以上方法中`static`用来获取`/static/`目录下的静态资源（例如 json、md 等文件）。下面是以上方法的参数说明：

参数 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
context | Vue实例，用来访问请求数据的Vue组件 | Object | -
url |API地址 | String | -
param | 请求参数 | Object | null
emulateJSON | 使用`application/x-www-form-urlencoded`类型发送请求数据 | Boolean | false
timeout | 设置本次请求的超时时间，单位`ms`, 为 0 时不设置超时 | Number | 0
requestKey | 标示某个请求，当同requestKey的请求再次发起时，会取消掉上次请求，为空时不启用该策略 | String | -

通过直接调用以下方法来使用缓存：
* `this.$service.cache.get(context, url, param, emulateJSON, lastModified, timeout)`
* `this.$service.cache.jsonp(context, url, param, emulateJSON, lastModified, timeout)`
* `this.$service.cache.post(context, url, param, emulateJSON, lastModified, timeout)`
* `this.$service.cache.static(context, url, param, emulateJSON, lastModified, timeout)`

以上方法中`static`用来获取静态资源（例如 json、md 等文件）。参数具体说明如下：

参数 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
context | Vue实例，用来访问请求数据的Vue组件 | Object | -
url |API地址 | String | -
param | 请求参数 | Object | null
emulateJSON | 使用`application/x-www-form-urlencoded`类型发送请求数据 | Boolean | false
lastModified | 上次请求数据的标识，如果与缓存中的标识不同则重新请求数据 | String | -
timeout | 设置本次请求的超时时间，单位`ms`, 为 0 时不设置超时 | Number | 0

`timeout`参数可以在启用插件时进行全局配置，默认的全局配置为`0`。

示例代码如下：
``` javascript
// 静态博客中获取 vue.md 如果有缓存则访问缓存
export default {
  data () {
    return {
      postUrl: '/posts/fontend/vue.md',
      postTimestamp: '2017-09-12 15:32'
    }
  },
  methods: {
    fetchData () {
      this.$service.cache.static(this, this.postUrl, {}, false, this.postTimestamp).then(data => {
        this.markdownText = data
      })
    }
  }
}
```

最后，该插件默认即在`main.js`中注册，代码如下：
``` javascript
import EzService from './services/ezService'

Vue.use(EzService, { timeout: 4000 })
```

