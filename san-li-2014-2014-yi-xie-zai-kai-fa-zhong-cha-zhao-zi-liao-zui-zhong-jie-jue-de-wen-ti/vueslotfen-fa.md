### 单个 slot

* ###### 子组件

```
<template>
  <button>这是默认显示的内容<slot></slot></button>
</template>
```

* ###### 父组件

```
<children>
   <span><br />这是分发的内容 <br /></span>
</children>
```

##### 单个slot时，自动匹配，位置随子组件位置改变



