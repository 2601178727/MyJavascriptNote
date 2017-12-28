```
history.back(-1)和history.go(-1)的区别
```

```
history.back(-1):直接返回当前页的上一页，数据全部消息，是个新页面
history.go(-1):也是返回当前页的上一页，不过表单里的数据全部还在
history.back(0) 刷新 history.back(1) 前进 history.back(-1) 后退
```

```
window.location.reload(); //刷新 
window.history.go(1); //前进 
window.history.go(-1); //返回 + 刷新 
window.history.forward(); //前进 
window.history.back(); //返回
```



