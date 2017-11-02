## Tabel 分页表格

### 概述
基础组件，主要用于展示大量结构化数据。

#### 使用
在模板中直接使用`v-table`标签即可，表格使用`slot`的方式去展现每一行。

#### 表格属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
columns | 表头项，对象，有`title`和`key` | Object | defalut
sourceListLength | 全部数据的长度 | Number | default
<!-- pagination | 前后台分页的选择项，为`true`时前台分页，`false`后台分页 | Boolean | true -->
tableBodyHeight | 表格body的高度，超过这个高度出滚动条 | String | 10em

#### 分页属性
属性 | 说明 | 类型 | 默认值
------------ | ------------- | ------------- | -------------
pageSizeOpts | 每页条数切换的配置 | Array | 5, 10, 20, 30
dataSourceLen | 全部数据的长度 | Number | 1
showPages | 显示几个页码 | Number | 7
showElevator | 显示电梯，可以快速切换到某一页 | Boolean | false
#### API
<!-- 前台分页数据更新通过触发`getRenderList`拿到数据，传过来的参数是个list就是分页后要渲染的数据 -->
分页数据更新通过触发`getRenderData`拿到`pagelist`, `currentPage`, `pageSize`,使用者使用`pagelist`里的`start`和`end`, 或者`currentPage`当前页和`pageSize`每页条数发请求拿数据