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

##### 说明：单个slot时，自动匹配，位置随子组件位置改变

### **具名slot**

* ###### 子组件

```
<template>
  <button>
    <slot name="first"></slot>这是默认显示的内容
    <slot name="second"></slot>
  </button>
</template>
```

* ###### 父组件

```
<children>
     <span slot="first">
       <br />这是分发的内容, first
      <br />
     </span>
    <span slot="second">
      <br />这是分发的内容, second
      <br />
     </span>
</children>
```

##### 说明：具名slot时，按照名称进行匹配，位置随子组件位置改变，相同名称按父组件位置排列，具名和非具名同时存在是子组件的solt对应所有未具名的父组件slot



