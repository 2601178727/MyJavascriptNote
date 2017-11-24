```
store.set('username', 'marcus')
store.get('username')
store.remove('username')

store.clear()

store.set('user', { name: 'marcus', likes: 'javascript' })

var user = store.get('user')
alert(user.name + ' likes ' + user.likes)

// Get all stored values
store.getAll().user.name == 'marcus'

// Loop over all stored values
store.forEach(function(key, val) {
    console.log(key, '==', val)
})
```

```
在登录页面请求接口拿到需要存储的值
store.set('orderList', res.data.data.order_list)


在需要使用数据的页面，通过mounted——页面加载后执行，拿到之前定义好的值
methods: {
    loadlist () {
      let orderList1 = store.get('orderList')
      console.log(orderList1)
    }
  },
  mounted () {
    this.loadlist()
  }
```



