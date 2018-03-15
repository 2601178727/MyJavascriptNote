```
// xxx.js 组件
exports.install = function (Vue, options) {
    Vue.prototype.ajax = function (){
        alert('aaaaaaa');
    };
};
```

```
// main.js 入口
import xxxx from './commons/xxxx'
Vue.use(xxxx);
```

```
// ccc.js 子组件
this.ajax();
```



