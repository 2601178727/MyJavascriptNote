

尽可能在开工前确定一套规范，并做好这套规范随时会进行修改的准备



1。全局设置字体、字号

2。 需要单独处理的需要统一到一个less文件中方便引用，并批量修改

格式

```
@url: '../../..';

// 头部顶标签
@fontFamily: SFUIText;
@fontSize: 14px;
```

引用

```
@import '../../assets/source.less';


  .videoContent {
    border: 1px solid #ddd;
    width: 100%;
    padding: @learnPadding;
    margin: @learnMargin;
    margin-top: @learnMarginTop;
    margin-bottom: @learnMarginBottom;
    
      background: url("@{url}/static/images/bg1.png");
```



  


