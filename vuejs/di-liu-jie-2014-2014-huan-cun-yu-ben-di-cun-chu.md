> 在单页应用的运作机制中，缓存是一个很重要的环节。
>
> 由于这类系统的前端部分几乎全是静态文件，所以它能够有机会利用浏览器的缓存机制，而比如动态加载的界面模板，也完全可以做一些自定义的缓存机制，在非首次的请求中直接取缓存的版本，以加快加载速度。
>
> 甚至，也出现了一些方案，在动态加载JavaScript代码的同时，把它们也缓存起来。比如Addy Osmani的这个[basket.js](https://github.com/addyosmani/basket.js)，就利用了HTML5 localStorage作了js和css文件的缓存。
>
> 在单页产品中，业务代码也常常会需要跟本地存储打交道，存储一些临时数据，可以使用[localStorage](https://github.com/mortzdk/localStorage)或者[localStorageDB](https://github.com/knadh/localStorageDB)来简化自己的业务代码。



