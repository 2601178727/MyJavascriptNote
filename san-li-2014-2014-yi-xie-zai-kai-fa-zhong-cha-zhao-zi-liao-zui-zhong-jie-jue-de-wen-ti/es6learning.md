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

> 利用这个特性，可以去除数组的重复元素。

```
function dedupe(array){
   return Array.from(new Set(array));
}
console.log(dedupe([1,2,3,3]));
```

> set 遍历

```
keys( )：返回一个键名的遍历器
values( )：返回一个键值的遍历器
entries( )：返回一个键值对的遍历器
forEach( )：使用回调函数遍历每个成员。
```

> 另一种去重操作

```
let arr=[3,5,2,2,5,5];
let unique=[...new Set(arr)];
console.log(unique);
```

> 延伸ES6 数组

```
Math.max(1,2,3,4) // 输出最大值
Math.max(...[1,2,3,4]) // 输出数组最大值
Math.max.apply(null, [1,[1,2,3],2,3,4]); // 输出数组最大值
```



