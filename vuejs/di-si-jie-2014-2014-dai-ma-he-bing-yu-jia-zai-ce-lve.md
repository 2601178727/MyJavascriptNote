> 人们对于单页系统的加载时间容忍度与Web页面不同，如果说他们愿意为购物页面的加载等待3秒，有可能会愿意为单页应用的首次加载等待5-10秒，但在此之后，各种功能的使用应当都比较流畅，所有子功能页面尽量要在1-2秒时间内切换成功，否则他们就会感觉这个系统很慢。
>
> 从这些特点来看，我们可以把更多的公共功能放到首次加载，以减小每次加载的载入量，有一些站点甚至把所有的界面和逻辑全部放到首页加载，每次业务界面切换的时候，只产生数据请求，因此它的响应是非常迅速的，比如青云的控制台就是这么做的。
>
> 通常在单页应用中，无需像网站型产品一样，为了防止文件加载阻塞渲染，把js放到html后面加载，因为它的界面基本都是动态生成的。
>
> 当切换功能的时候，除了产生数据请求，还需要渲染界面，这个新渲染的界面部件一般是界面模板，它从哪里来呢？来源无非是两种，一种是即时请求，像请求数据那样通过AJAX获取过来，另一种是内置于主界面的某些位置，比如script标签或者不可见的textarea中，后者在切换功能的时候速度有优势，但是加重了主页面的负担。
>
> 在传统的页面型网站中，页面之间是互相隔离的，因此，如果在页面间存在可复用的代码，一般是提取成单独的文件，并且可能会需要按照每个页面的需求去进行合并。单页应用中，如果总的代码量不大，可以整体打包一次在首页载入，如果大到一定规模，再作运行时加载，加载的粒度可以搞得比较大，不同的块之间没有重复部分。



