> 很明显，前端JS渲染由于违背了浏览器的优化策略，总是存在一个不可突破的瓶颈：
>
> JS和数据没加载完，JS拼装数据的逻辑没执行完，浏览器不能开始正常的渲染流程。
>
> 这个性能差异我感觉短时间内这种JS渲染的webapp是无法跟传统页面输出模式相比较的，因为浏览器的各种渲染优化策略基本上都是围绕着传统页面时序展开的。有没有办法突破这个性能瓶颈，并且兼顾SEO，但还保留单页面应用的体验呢？
>
> 答案是：有办法。
>
> 有人或许会想到 [Isomorphic Javascript](http://nerds.airbnb.com/isomorphic-javascript-future-web-apps/)，所谓的同构JavaScript，或者什么前后端模板复用，相信我，这个概念根本就是扯淡！
>
> 其实办法很简单，根本用不着同构JS，页面还是服务端拼装好的，CSS在head中，主文档是完整的HTML，JS在body尾部；但需要在后端模板中实现一种功能：允许通过特殊的ajax请求以json格式响应页面中的局部区域。这项技术被称为 [Quickling](http://www.slideshare.net/ajaxexperience2009/chanhao-jiang-and-david-wei-presentation-quickling-pagecache)。
>
> 此外，单页面应用还有一项优化手段，叫PageCache，前端控制页面切换时，把之前的页面缓存到内存中，下次再回到这个页面就直接展现，不用再次请求数据拼装模板渲染，进一步优化用户在站内浏览的体验。
>
> 基于Quickling和PageCache我们在印度市场（网络环境超差）实现了两个单页面应用产品：[YoloSong](http://music.uodoo.com/index?uc%3Cem%3Eparam%3C/em%3Estr=dnfrpfbivesscpgimibtbmntnisieijblauputoggd) 和 [Huntnews](http://huntnews.in/p/index?uc%3Cem%3Eparam%3C/em%3Estr=dnfrpfbivesscpgimibtbmntnisieijblauputoggdnw) ，其优化点：
>
> * * 首次访问服务端渲染，页面间Quickling切换，单页面体验
>   * 所有链接可爬取，解决SEO问题
>   * PageCache缓存已访问页面，加速切换，历史记录前进后退
>   * 可 
>     **全站禁用JS**
>     ，不影响浏览体验
>   * 按需加载，请求合并



