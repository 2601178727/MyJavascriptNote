

```
pop 方法

移除数组中的最后一个元素并返回该元素。 
arrayObj.pop( ) 必选的 arrayObj 引用是一个 Array 对象。 
说明 
如果该数组为空，那么将返回 undefined。
```



```
shift 方法
移除数组中的第一个元素并返回该元素。
arrayObj.shift( )
必选的 arrayObj 引用是一个 Array 对象。
说明
shift 方法可移除数组中的第一个元素并返回该元素。

```



代码如下:

var arr = new Array\(0,1,2,3,4\); 

var remove = arr.pop\(\); 

alert\(remove\); 

alert\(arr.length\);

移除并返回最后一个元素，先弹出 4 ，然后提示目前数组长度 弹出 4 ！

  


```
push 方法
将新元素添加到一个数组中，并返回数组的新长度值。
arrayObj.push([item1 [item2 [. . . [itemN ]]]])
参数
arrayObj
必选项。一个 Array 对象。
item, item2,. . . itemN
可选项。该 Array 的新元素。
说明
push 方法将以新元素出现的顺序添加这些元素。
如果参数之一为数组，那么该数组将作为单个元素添加到数组中。
如果要合并两个或多个数组中的元素，请使用 concat 方法。
```



代码如下:

var arr = new Array\(0,1,2,3,4\); 

// 参数是一个或多个 

var len = arr.push\(5,6\); 

//len = arr.push\(7\); 

for\(var i=0;i&lt;arr.length;i++\){ 

    alert\(arr\[i\]\); 

}

  


可以一次性增加多个进去，也可以增加一个，返回数组目前长度。变了打印数组内容观察变化！



```
splice 方法
从一个数组中移除一个或多个元素，如果必要，在所移除元素的位置上插入新元素，返回所移除的元素。
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])
参数
arrayObj
必选项。一个 Array 对象。
start
必选项。指定从数组中移除元素的开始位置，这个位置是从 0 开始计算的。
deleteCount
必选项。要移除的元素的个数。
item1, item2,. . .,itemN
必选项。要在所移除元素的位置上插入的新元素。
说明
splice 方法可以移除从 start 位置开始的指定个数的元素并插入新元素，
从而修改 arrayObj。返回值是一个由所移除的元素组成的新 Array 对象。


```



代码如下:

var arr = new Array\(0,1,2,3,4\); 

// 删除从2开始的两个元素，位置从0开始 

// 返回移除元素的数组 

var reArr = arr.splice\(2,2\); 

// 可以在移除元素的位置替换新的元素进去 

//只是从移除开始位置进行增加新元素，如果你移除两个元素，你完全可以增加10个新元素进去 

//var reArr = arr.splice\(2,2,6,7,8,9\); 

for\(var i=0;i&lt;arr.length;i++\){ 

    alert\(arr\[i\]\); 

}



如果你不想增加新的元素进去，那么不要传递第三个参数即可！



```
concat 方法 (Array)
返回一个新数组，这个新数组是由两个或更多数组组合而成的。
array1.concat([item1[, item2[, . . . [, itemN]]]])
参数
array1
必选项。其他所有数组要进行连接的 Array 对象。
item1,. . ., itemN
可选项。要连接到 array1 末尾的其他项目。
说明
concat 方法返回一个 Array 对象，其中包含了 array1 和提供的任意其他项目的连接。
要加的项目（item1 … itemN）会按照从左到右的顺序添加到数组。
如果某一项为数组，那么添加其内容到 array1 的末尾。
如果该项目不是数组，就将其作为单个的数组元素添加到数组的末尾。
以下为从源数组复制元素到结果数组：
对于从正被连接到新数组的数组中复制的对象参数，复制后仍然指向相同的对象。
不论新数组和源数组中哪一个有改变，都将引起另一个的改变。
对于连接到新数组的数值或字符串，只复制其值。一个数组中值有改变并不影响另一个数组中的值。

```



代码如下:

var arr = new Array\(0,1\); 

var arr2 = new  Array\(3,4\); 

var arr = arr.concat\(arr2\); 

for\(var i=0;i&lt;arr.length;i++\){ 

    alert\(arr\[i\]\); 

}



方法的作用是将arr2中的元素复制到了arr中！

