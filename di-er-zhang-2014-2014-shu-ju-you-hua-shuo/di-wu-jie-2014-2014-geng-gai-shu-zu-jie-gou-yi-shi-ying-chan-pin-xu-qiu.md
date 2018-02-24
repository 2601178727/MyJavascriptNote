```
应用场景： 当需要分行排列数据时，我们有需要将数组以特定的规则进行二次拆分，以供使用，这里封装了一个函数
```

```
reData (oldContent, number) {
      let num = oldContent.length
      let netData = new Array()
      let ai = 0
      while (ai < num) {
        let nai = ai + number
        netData.push(oldContent.slice(ai, nai))
        ai += number
      }
      return netData
    }
```

```
oldContent：需要拆分的数组
number： 几条数据为一行
```



