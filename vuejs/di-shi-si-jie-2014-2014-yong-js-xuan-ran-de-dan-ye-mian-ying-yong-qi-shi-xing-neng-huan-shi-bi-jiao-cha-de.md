> ![](https://cloud.githubusercontent.com/assets/536297/9624743/1e7c38b8-5182-11e5-81c9-6dafc7587978.png "image")如[上图](https://docs.google.com/presentation/d/1IRHyU7%3Cem%3EcrIiCjl0Gvue0WY3eY%3C/em%3EeYvFQvSfwQouW9368/present?slide=id.gc57996a9_046)，浏览器通过网络请求加载页面资源，在页面呈现之前无论如何都要经历以下过程：
>
> 1. HTML→DOM
> 2. CSS→CSSOM
> 3. DOM + CSSOM → Render Tree
> 4. 对Render Tree进行布局计算\(Layout\)
> 5. 对布局结果进行屏幕绘制\(Paint\)
>
> 如果在JS渲染页面模式下，需要在前端用JS加载样式并组装数据生成HTML插入页面，以上浏览器渲染过程必须等到页面加载完CSS，并且JS加载完数据拼装好HTML之后才能开始进行，一般的网络时序如下：

![](https://cloud.githubusercontent.com/assets/536297/9624818/f2132f92-5182-11e5-94c5-1b7143779a41.png "image")

> 大概阐述一下这个流程：
>
> 1. 浏览器发起请求加载主文档
> 2. 服务端响应一个基本骨架的主文档
> 3. 浏览器加载主文档中外链的loader.js（根据路由控制资源加载的）
> 4. 服务端响应loader.js
> 5. loader.js执行，根据页面url判断用户访问到哪个虚拟页面，然后再发起请求加载对应页面的js和css
> 6. 页面所需JS和CSS都加载完毕，JS执行，发起请求加载数据
> 7. 数据加载完毕，JS执行前端模板拼装，插入DOM节点，然后浏览器开始前述渲染过程
> 8. 最终页面呈现
>
> 概括一下，加载时序大概是这样的：

![](https://cloud.githubusercontent.com/assets/536297/9624911/cf5cc4d0-5183-11e5-9e50-0ff3a49973c0.png "image")

> 以上加载过程均为串行，需要至少多付出3次RTT。如果把这种架构应用在高延迟的网络环境下（比如移动2G），那就是找死啊（其实国内现在的网络环境很好了，这样搞问题或许不太明显）。
>
> 当然，上面的例子还是常规了一些，有些请求可以适当合并，进一步优化之后，大概可以搞成这个样子：

![](https://cloud.githubusercontent.com/assets/536297/9624994/c258727e-5184-11e5-9f84-626723494265.png "image")

> 就是首次请求的主文档尽量多内嵌一些东西，除了HTML骨架之外，把loader.js内嵌，再加一个loading界面，让用户觉得没那么长时间白屏，另外如果前端路由切换是pusState控制的话，可以在服务端知道前端路由url，然后在主文档中直接内嵌数据，主文档体积大了不少，但是可以减少2次RTT，优化对比：

![](https://cloud.githubusercontent.com/assets/536297/9625044/322247d8-5185-11e5-849e-288fe0492d0e.png "image")

> 当然，如果你的单页面应用体量很小，完全不用按需加载，主文档内嵌一切可以再减少一次RTT，得到：
>
> ![](https://cloud.githubusercontent.com/assets/536297/9625075/7530182a-5185-11e5-9ddf-27861731bbda.png "image")
>
> 不过这么极端的做法其限制就是：你的应用千万不能太大！
>
> 前端渲染模式我厂的代表产品：[UC奇趣百科](http://qiqu.uc.cn/?uc%3Cem%3Eparam%3C/em%3Estr=frpfvedncpssntnwbi#!/index/index) ，其优化点：  
> \* 主文档loader.js内嵌、数据内嵌、loading界面内嵌  
> \* 页面资源按需加载，请求动态合并  
> \* localstorage存储JS/CSS
>
> 在国内的网络环境下感觉还OK吧。。。



