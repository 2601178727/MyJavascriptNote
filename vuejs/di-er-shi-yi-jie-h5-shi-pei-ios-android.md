```
let u = navigator.userAgent
export default {
  isAndroid: u.indexOf('Android') > -1, // android终端
//   isAndroid: u.indexOf('Android') > -1 || u.indexOf('Linux') > -1, // android终端或者uc浏览器
  isiOS: !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/) // ios终端
}
```



