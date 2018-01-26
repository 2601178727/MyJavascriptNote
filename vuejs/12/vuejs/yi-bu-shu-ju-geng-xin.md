```
//改变数据
vm.message = 'changed'

//想要立即使用更新后的DOM。这样不行，因为设置message后DOM还没有更新
console.log(vm.$el.textContent) // 并不会得到'changed'

//这样可以，nextTick里面的代码会在DOM更新后执行
Vue.nextTick(function(){
    console.log(vm.$el.textContent) //可以得到'changed'
})

作者：知乎用户
链接：https://www.zhihu.com/question/50879936/answer/123125629
来源：知乎
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```



