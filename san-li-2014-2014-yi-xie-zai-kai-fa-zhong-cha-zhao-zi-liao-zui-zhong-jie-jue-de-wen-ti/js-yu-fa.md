# [梳理一下JS的基本语法](http://www.cnblogs.com/zhaowenxin/p/5962324.html)

### web三层结构来说

```
结构层：HTML         从语义角度，描述页面结构
 样式层：CSS          从审美的角度，美化页面
 行为层：JavaScript   从交互的角度，提升用户体验
 
js:用来制作web页面的交互效果，提升用户体验
```

# 语法概述

### 一、JS引入3种的方式：

     1.内嵌引入，但不建议

    2.通过`<script async='async'>`标签引入，可放在head里面，为减少加载时间，一般放在body最后
    3.建议通过link引入

    <script>标记的属性：
    type="text/JavaScript"可以省略

    Sync:同步，一个人有序的做多件事

    Async:异步，多个人有序的做多件事情

    async='async'和defer='defer'都是异步下载，区别在：

    async='async'是立即异步下载外部JS，不影响页面其它的操作，js下载完毕立即执行；

    defer='defer'是在js，css整个文档都下载完后再执行，只有外部脚本可以使用

### 二、五种数据类型：

##### 1.字符串类型string（""）

```
注意：引号既可以用单引号，也可双引号 --建议单引号
a,如果字符串中有单引号，就用可引号

b,如果字符串内容中单双引号都有，就用转译符,在引号前用。常用的转译符有：\"、换行\n、缩进\t
```

##### 2.数值类型number：没有被引号引起来的数字：整数、负数、小数...\(123\),表示一种数据的量

##### 3.布尔值类型boolean

```
boolean在内存中存储的格式： boolean在存储的时候会将ture转成1，false转成0

 
var a =ture;  
var b ="ture";
var c = a == b;
console.log(c); //输出false
```



