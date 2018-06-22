## ES6 set

> 它类似于数组，但是成员的值都是唯一的，没有重复的值。Set本身是一个构造函数，用来生成Set数据结构。

```
add(value):添加某个值，返回Set结构本身。
delete(value)：删除某个值，返回一个布尔值，表示删除是否成功。
has( value)：返回一个布尔值，表示参数是否为Set成员。
clear( ):清除所有成员，没有返回值。
```

> Array.from方法可以将Set结构转为数组。

```
var items = new Set([1,2,3,4,5]);
var array = Array.from(items);
console.log(array);
```



