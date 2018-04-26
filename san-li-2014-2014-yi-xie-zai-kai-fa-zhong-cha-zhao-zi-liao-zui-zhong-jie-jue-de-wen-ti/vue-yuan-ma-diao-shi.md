###### vue源码调试踩坑记录



**目的: 可以断点调试vue的源代码, 研究一个`new vue({...})`以及data的更新在vue源码内部是如何运行的**

**目前做到了, 其实比较简单, 也不知道为什么会弄了一天…**

遇到的问题有2个, 其中一个是坑

一:

其实`git clone repo`-&gt;`npm install`-&gt;`npm run setup`-&gt;`npm run dev`就可以了,

但是问题发生在`rollup-plugin-alias`这个插件

`vue`目前`@2.5.9`的-dev用的`rollup-plugin-alias`是`^1.3.1`

里面关于别名有一个bug是win10下生成的alias在最后一个路径的/会变成\

类似`../src/dev/config\index.js`

解决这个问题方法有2个

\(1\)升级`rollup-plugin-alias`至`^1.4.0`  
\(2\)在`node_module`里面改`rollup-plugin-alias`的源码\(只需要改一行\)

二:

找到网上大多数解决方案都是调试打包后的源代码\(1万行那种umd\)

在F12后要看见vue项目`src/core`里面那些`instance`文件夹的代码, 好像没有找到

于是了解了一天vue采用的打包工具rollup

最后解决了

## 正文: {#正文}

#### **以下是 “手把手截图记录步骤”** {#以下是-手把手截图记录步骤}

\(1\) 运行`git clone https://github.com/vuejs/vue.git`

\(2\) 运行`npm install & npm run setup`

\(3\)**如果你电脑不是win10就跳过这一步**

运行`npm run dev`会报错如图:  
![](https://img-blog.csdn.net/20171209230301773?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvUmV1c0xp/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast "rollup报错")

解决方法,找到  
`\node_modules\rollup-plugin-alias\dist\rollup-plugin-alias.js`

这个文件, 如下修改

```
return
 {
    resolveId: 
function
(importee, importer)
 {
var
 importeeId = normalizeId(importee);
      
var
 importerId = normalizeId(importer);

      
// First match is supposed to be the correct one
var
 toReplace = aliasKeys.find(
function
(key)
 {
return
 matches(key, importeeId);
      });

      
if
 (!toReplace) {
        
return
null
;
      }
      
// 以下是需要修改的地方
// var entry = options[toReplace]; 把这一行改成下面这样
var
 entry = normalizeId(options[toReplace]);

```

\(4\) 找到`\build\config.js`文件

把`genConfig`函数的`config`变量加一个属性`sourceMap: true`如图:

![](https://img-blog.csdn.net/20171209230759821?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvUmV1c0xp/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast "修改rollup配置属性")

\(5\) 运行`npm run dev`

\(6\) 打开`\examples\commits\index.html`,开始断点调试, 如图:

![](https://img-blog.csdn.net/20171209231003887?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvUmV1c0xp/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast "这里写图片描述")

在运行`npm run dev`下, 每一次修改`\src\core`的文件, 都会在`\dist`目录下生成新的`vue.js`, 这样直接引入`\dist\vue.js`就可以调试了.

