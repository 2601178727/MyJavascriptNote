##### 网址：[http://admin.myhbp.org.cn/hmmchina](http://admin.myhbp.org.cn/hmmchina) {#一-技术栈}

##### 一、技术栈 {#一-技术栈}

---

```
- vue

- vue-router

-element-UI (依赖vue)

-webpack

-echarts

-less
```

##### 二、用到的技术 {#二-用到的技术}

---

> vue

* slot 分发
  * 普通分发
  * 带参数的分发
* ref
* export
* Promess
* 父子组件传值、传递事件

> vue-router

* 路由懒加载

```
普通路由：
importContentSort from'@/page/ContentSortPage/index'
懒加载路由：

const ContentSort = ()=>import('@/page/ContentSortPage/index')
```

* 路由守卫

```
和methods
同级：


  beforeRouteEnter (to, from, next) {
    API.post('api/insights/lists').then(
      (res) =>{
next(vm =>{
let sortData = res.get
(
'data.data.topicList'
)
          sortData.forEach((item, 
index
) =
>
 {
            item.text = item.topic_name
            item.value = item.id
          })
          sortData.unshift({
            tex
t:
vm
.$t(
'message.contentinsight.all'
)
          })


vm
.viewData = 
vm
.loadViewData(sortData)
        })
      }
    )
  }
```

> element-UI

* table
  * render （表头重构）
  * 自定义筛选
  * 复合筛选

> webpack

* 自动化打包

> echarts

* resize （重新计算尺寸）
* dispose （重新绘图）

> less

* 定义属性值

```
App.less
文件
// 
按钮圆角
@_buttonRediosGlobal
: 
4
px;
```

* 定义样式类

```
App
.less
文件
.global-edit-btn
() {

border-radius
: 
@_buttonRediosGlobal
;

padding
: 
@_buttonTablePaddingGlobal
;

font-size
: 
@_buttonTableFontSize
;

border
: 
0
;

margin-left
: 
5px
;

margin-bottom
: 
5px
;

background-color
: 
#e5ecf4
;

color
: 
#448aff
;
};
```

* 引用

```
@import
'./../../assets/App.less'
;



.userTable
{

margin-top
: 
@_tableMarginTop
; 
// 
引用属性值
.global-edit-btn
,

.global-edit-btn
:focus
 {

.global-edit-btn
(); 
// 
引用样式类

    }

.global-delete-btn
,

.global-delete-btn
:focus
 {

.global-delete-btn
();
    }
}
```

##### 三、开发上的反思 {#三-开发上的反思}

* 代办事项一览表

###### 在做什么？还有多久完成？有没有什么困难？ {#在做什么还有多久完成有没有什么困难}

```
如何能有条不紊的回答上述问题？
表头：
功能、板块、类别、状态、负责人
需要配合人员、结束时间、预计时间、优先级、备注
在做什么？
优先级（
1
~
9
），现在正在做优先级为
1
的
n
条
接下来需要做优先级为
2
的
m
条
还有多久完成？
预计时间求和即可
有没有什么困难？
需要配合人员
```

* 版本文档 （让产品经理周知产品更新迭代功能）

```
## 
版本号：
1.1
.5

###### 
发布时间：
8
/
5
/
18


#### 
更新内容
1.
优化了后台打开速度，目前打开后台耗时
1.5
S

2.
班级管理下查看学员、班主任详情改为弹窗展示
3.
统一全站圆角为
4
px

4.
统一全站相同类型按钮样式
统一全站相同类型按钮样式
```

* 功能、权限一览表

```
表头：
板块、页面、功能、身份、是否可见
是否具有权限、是否开发、备注
```

* 控制中心文件

```
config
.js


---

let 
path
 = 
''

let terminal = 
''


// 
开发环境与线上环境资源服务器对应
if
 (process.env.NODE_ENV === 
'development'
) {

path
 = 
'http://10.154.7.122/'

  terminal = 
'development'

  // 
path
 = 
'http://101.132.139.245:82/'

} 
else
 {

path
 = 
'http://101.132.139.245:82/'

  terminal = 
'production'

}

export const 
config
 = {
  server: 
''
,
  terminal: terminal,

path
: 
path
,
  disListCount: 
10
,
  topUserCount: 
50
,
  hotCommentsCount: 
50
,

  exportExcel: 
false

}
export default 
config
```

* 组件思想 （万物皆组件）
* 笔记（好记性不如烂笔头）

##### 四、产品思想上的反思 {#四-产品思想上的反思}

* 体验、管理用户期望值

```
    loading
动画是很好的改善用户体验、管理用户期望值得方式
除移动端新闻类展示形式外，分页更优于
loadmore
，能让可和直观感受到总体
```

* 速度

```
当下时代，产品的打开速度是硬性要求，其次是内容展现
可以借助路由懒加载只在需要的时候才加载相关页面
需要遵守一个准则，所有的接口只有在需要用的时候才请求
```

* 统一

```
产品需要有一套统一的UI规范，
前端需要根据
UI
规范，实现统一的风格开发
可以借助
less
开发控制中心文件
```



