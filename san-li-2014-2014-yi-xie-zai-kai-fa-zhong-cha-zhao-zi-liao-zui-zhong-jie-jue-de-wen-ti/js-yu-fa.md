# 梳理一下JS的基本语法

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

##### 4.undefined：声明变量没有赋值

##### 5、Null:空的对象

```
特殊：NaN(not a number):number的一种。
  // 判断NaN:IsNaN翻译：是一个非数字：如果是数字ture
  //        var a ="abc";
  //        var b =123;
  //        console.log(a-b);
  //        console.log(isNaN(a-b)); // 输出ture
  // 作用：用来表示数字的一种不正常的状态（一般会在计算出现错误时出现）。
​
// 特殊：特殊到自己都不等于自己
  var a =NaN;  
  var b =NaN;
  var c = a === b;
  console.log(c); //输出false 

技巧：判断数据的类型：typeof（变量/直接量） 可省略括号：typeof变量/直接量
```

### 三、变量：用来存储数据的内存

```
内存：运行内存（电脑运行的同时可以保存数据，断电后清空）  
       内存条：加大运行内存
       硬盘：存储空间的大小 4G 32G  (断电不会清空)
```

```
输出的方式：
alert()：弹出一个提示信息框 - 位置不能改变，不能拖动，不能关闭。其实浏览器的进程已经被暂停了 -- 只能在任务管理器来关闭。

console.log() 向控制台输出内容 作用：用于代码的调试 应用：招聘

prompt()输入框：使用浏览器输出自己输入的内容

a.声明变量：创建变量 var a
  var:声明变量的关键字  a:变量名

b.给变量赋值：a="123" =赋值运算符。作用：等号右边结果赋值等号左边的变量
    var a = "123" 
    var b = "456+123"
    console.log(a);  
    console.log(b)
    console.log(a+b)

c.变量名的命名规则：
1）变量必须以字母开头

 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做） 

class，id的命名规则：只能由英文字母、数字、下划线以及连接符组成，并且数字不能放在开头

 如果名称以下划线开头，那么后面直接跟数字也是可以的；class,id不可以

2）变量的命名，不能使用javascript中的关键字和保留字 关键字：已经被javascript内部使用过的 保留字：还未被javascript内部使用过，但可能有一天会被用到（备胎）。

3）区分大小写

d.变量的类型由变量的赋值来决定的
 var a ="123"; 
 console.log(typeof a);  -- 控制台显示string
 var b =123; 
 console.log(typeof b);  -- 控制台显示numbe
```

### 四.运算符\(操作符\)：

```
1.运算符的简写：
    var a ;
    a = 10;
等价于 var a =10;

2.自增自减运算符：b++;//a+=1;a=a+1
     var a = 2;
     var b = 3;
     var c = a++ + b++;
    //a++:a = a+1;
    //后加：先进行运算，再加1
    //var c = a+b;a=a+1;b=b+1;
    var d = ++a + ++b;
    console.log(a);
    console.log(b);
    console.log(c);   //输出5
    console.log(d);   //输出7

3.逻辑运算符：
优先级：!非  >  &&与 > ||或  
#&&操作符：求第一个操作数的布尔值，如果这个布尔值为true，那么最终的返回值就是第二个操作数，否则输出第一个
||操作符：求第一个操作数的布尔值，如果这个布尔值为true，那么最终的返回值就是第yi个操作数，否则最终的返回值为第er个操作数。
短路操作：在&&和||中，如果第一个操作数就已经能确定最终返回的结果，那么就不会去计算第二个操作数了
4.比较运算符(关系运算符)：
1、>
2、<
3、>=
4、<=  
5、== 是否相等，仅仅是数据的内容，没有判断数据的类型
6、=== 判断是否全等
7、！= 不等于
8、！== 不全等

5.赋值运算符：= 作用：等号右边结果赋值等号左边的变量
6.逗号运算符： --省略var
    var a,b,c;
    a=b=c=1;

7.条件运算符（三目运算符/三元运算符）
    结构：bolean表达式？操作一：操作二；
    var a=15;
    var b=16;
    var c=24;
   //判断a和b的大小
    a>b?alert(a):alert(b);
   //判断a是否大于b，如果a大于b成立，输出a；否则输出b  --即if else的简写
  //判断a,b,c的大小
    (a > b ? a:b) > c ? alert(a > b ? a:b):alert(c);
   //先找出a和b中的大的，再与c比较

注：优先使用全等和不全等的操作符！
```

### 六.运算符：

```
1. +号： 加号的作用:
    a,连接两个字符串，连接作用  
    b,两个数值中间的+，是运算作用
    c,字符串与数值之间的+，是连接
2.-减：两个number间的操作
3.*乘：两个number间的操作
4./除：两个number间的操作
5.%取余(取模)：两个number间的操作
6.10取余（取模）3
7.()作用：改变计算优先顺序
8.Math对象（面向对象；万物皆对象）万物皆盒子
 1）Math.pow(a,b); //得到a的b次方
 2）Math.round(a); //四舍五入
 3）Math.ceil(a);  //向上取整
 4）Math.floor(a);  //向下取整
 5）Math.max(a,b,c); //取三个数中的最大值
 6）Math.min(a,b,c);  //
 7）Math.random();  //生成随机数（0-1之间）
   拓展：生成1-50的随机数
    var f =Math.random()*49+1;                        
    console.log(f);
 8）Math.pow(a,1/3);//立方根
    var a = Math.pow(2,10);
    console.log(a);
    var b =Math .round(3.38);
    console.log(b);
```

### 七.运算符的优先级

```
运算符                                    描述                        
 ++ -- - + ~ ! delete new typeof void   一元运算符、返回数据类型、对象创建、未定义值    
 * / %                                  乘法、除法、取模                  
 + - +                                  加法、减法、字符串连接               
 << >> >>>                              移位                        
< <= > >= instanceof                    小于、小于等于、大于、大于等于、instanceof
== != === !==                           等于、不等于、严格相等、非严格相等         
 &&                                     逻辑与                       
                                      逻辑或                       
?:                                      条件                        
=                                       赋值、运算赋值                   

下表按从最高到最低的优先级列出JavaScript运算符。具有相同优先级的运算符按从左至右的顺序求值。
```

### 八.数据类型的转换：强制转换和隐形转换

```
8.1强制转换：
8.1.1 转Number（字符串/boolean）
 通过prompt输入的数据类型是string,不管是123，还是具体的汉字
 var a=prompt("请输入一段内容");//输入4 
  var b =a+1;
  console .log(b);//输出41
//想要输出5：
var a=prompt("请输入一段内容");
a=number(a);//将原来的字符串a转换成number类型
var b =a+1;
console .log(b);//输出5
console.log(typeof (a));//输出number
特点：
a,如果要转换成数字，输入的内容必须是纯数字，否则NaN.
b、如果内容是空的，转换成0
c、如果是小数，小数会保留
d、如果字符串中包含非以上格式，则将其转换为NaN

8.1.2 转Number，parseInt 转换
    var a ="123.abc";
    a = parseInt(a);
    console.log(a);//输出123
    console.log(typeof (a));//输出number
特点：a、如果有小数，会直接去掉小数。
    b、如果第一个是数字，就继续解析直至字符串完毕或者遇到非数字符号为止

8.1.3 parseFloat():转数字
与parseInt一样：唯一区别：能保留小数
8.1.4 boolean转成number
    var a = true;
    a = Number(a);
    console.log(a);
    console.log(typeof (a));
8.2字符串的转换：
8.2.1 数值转字符串 法一
   var a = 123;
    a = a.toString();
    console.log(a);
    console.log(typeof (a));//string

直接调用.toString方法可以将内容直接转成字符串

8.2.2 数值转字符串 法二
  var a = 123;
    a = string(a);
    console.log(a);
    console.log(typeof (a));//string

直接将要转的内容放在string后的括号中

区别：一是直接调用这个变量对象的方法, 第二个是强制转换

8.2.3 boolean转string
    var a = true;
    a = Boolean(a);
    console.log(a);
    console.log(typeof (a));
  注意：除了false、空字符""、0、NaN、undefined在转换时会转成false，其余都会转成true

8.3隐式转换：不通过程序猿去写固定代码，浏览器可以直接进行转换
8.3.1隐式转换成Number:直接在要转换的内容前加上+-*\%
  +a a-0 a*1 a/1 a%1
    var a = "123";
    a = +a;
    b = a\1;
    console.log(a);
    console.log(b);
    console.log(typeof (a));
    console.log(typeof (b));
8.3.2 隐式转换成string:直接在要转换的内容hou加上""
   var a = 123;
    a = a + "";
    console.log(a);
8.3.3 隐式转换成boolean:直接将a = !！a;或者！a
```

### 九、代码注释：

```
源码中被JavaScript引擎忽略的部分就叫做注释，它的作用是对代码进行解释。Javascript提供两种注释：一种是单行注释，用 // 起头；另一种是多行注释，放在 /* 和 */ 之间。

只有在js创建的时间，在函数时，推荐使用多行注释/** */。其余时间多行注释易出现问题

注：虽然js代码虽然对空格、换行、缩进不敏感，但一定要注意书写。建议既加分号，又换行 - 可读性更强
```

##### 一、流程控制：

```
1、if结构 ：用于判断某些条件是否执行
  if_else: 可以判断2个条件
  if_else if_else 判断多个条件
    var a = prompt("带了多少钱");
    if(a>300){
        console.log("你的钱超过了300，请吃饭");
    }
   else if(a>200){
       console.log("你的钱不够300，够200，请吃快餐");
     }
   else{
        console.log("明天记得带够");
    }
    console.log("程序结束")2016.10.13 18:06:39 2016.10.13 18:06:41 2016.10.13 18:06:43 2016.10.13 18:06:44 
注意：
大括号后不能加分号

程序运行到if之后，判断if括号里的条件，如果条件满足，则执行内容；如果不满足，就不会执行；只会执行一个！

#注意：
a、大括号后不能加分号；

b、代码不支持连写：90<pj<100,只能90<pj&&pj<100;

2、switch case结构:作用是与else if是一样的，
   var a = prompt("请输入今天星期几对应的数字");
    switch (a) {
        case "1":
            alert("您输入的是星期一");
            break;
        case "2":
            alert("您输入的是星期二");
            break;
        case "3":
            alert("您输入的是星期三");
            break;
        case "4":
            alert("您输入的是星期四");
            break;
        case "5":
            alert("您输入的是星期五");
            break;
        case "6":
            alert("您输入的是星期六");
            break;
        case "7":
            alert("您输入的是星期日");
            break;
        default:
            alert("你输入什么鬼");
    }
```

##### 二、控制台的sources看源码

```
a，打开要查看的页面
b,打断点，刷新页面，会发现命中了断点
c，鼠标放在变量名上，会发现输入值
```

### JS背景

```
-1995年，Netscape公司开发一个脚本语言，叫LiveScript,用于做验证的。为了推广，利用当时最火的Java词汇，改名JavaScript.-netscapt是第一款浏览器

03年以前，牛皮癣广告，很被排斥

04年谷歌用js技术来做ajax技术

07年，乔布斯发布第一代苹果，移动端页面开始发展

10年，html5推出画布--做游戏。例：切水果

11年，node.js诞生，js从移动端铺开服务器端
```

### 浏览器是如何工作的：

```
http://www.2cto.com/kf/201202/118111.html

浏览器引擎，用来查询和操作渲染引擎

渲染引擎：用来显示请求的内容，负责解析html和css

Javascript interpreter：js解析器，负责执行js

notworking网络：负责发送网络请求

JavaScript语言：
是世界上用的最多的脚本语言。脚本语言：不需要编译，直接运行时边解析边执行的语言

编译：一次性把所有代码转换成cpu可以看懂的语言，一行一行执行

解释：一行一行解析，解析一行执行一行

js是一种客户端的脚本语言

js组成：ECMAScript、DOM、BOM
ECMAScript:js的语法规范

DOM：js操作网页上元素的API

BOM:JS操作浏览器部分功能的API
```



