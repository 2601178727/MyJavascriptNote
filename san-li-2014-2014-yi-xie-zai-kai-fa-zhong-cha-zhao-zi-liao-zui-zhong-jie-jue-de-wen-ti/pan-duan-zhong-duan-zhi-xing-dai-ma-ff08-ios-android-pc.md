#### 应用场景

```
App 下载引导页，不同终端不同逻辑
```

#### 代码

```
$(function() {
    var u = navigator.userAgent;
    var ua = navigator.userAgent.toLowerCase();
    var isAndroid = u.indexOf('Android') > -1 || u.indexOf('Adr') > -1; // android终端
    var isiOS = !!u.match(/\(i[^;]+;( U;)? CPU.+Mac OS X/);             // ios终端
    var innerWidth = window.innerWidth                                  // 屏幕尺寸

    if (innerWidth > 768) {                                             // 大于768尺寸的PC
        $(".ios-btn ").bind('click', function(event) {                  // Pc click事件
            window.location.href = 'https://itunes.apple.com/cn/app/id1332197484'
        });
        $(".android-btn ").bind('click', function(event) {
            window.location.href = 'http://app.myhbp.org.cn/android/%E5%93%88%E4%BD%9B%E7%AE%A1%E7%90%86%E5%AF%BC%E5%B8%88.apk'
        });
    } else {
        if (ua.match(/MicroMessenger/i) == "micromessenger") {          // 微信内置浏览器
            if (isiOS) {                                                // ios终端
                $(".ios-btn ").bind('touchstart', function(event) {     // 移动 touchstart 事件
                    $(".dialog-model").css("display", "block")
                });
                $(".android-btn ").bind('touchstart', function(event) {
                    return
                });
            }
            if (isAndroid) {
                $(".ios-btn ").bind('touchstart', function(event) {
                    return
                });
                $(".android-btn ").bind('touchstart', function(event) {
                    $(".dialog-model").css("display", "block")
                });
            }

        } else {                                                        // 移动浏览器
            if (isiOS) {
                window.location.href = 'https://itunes.apple.com/cn/app/哈佛管理导师/id1332197484'
                $(".ios-btn ").bind('touchstart', function(event) {
                    window.location.href = 'https://itunes.apple.com/cn/app/哈佛管理导师/id1332197484'
                });
                $(".android-btn ").bind('touchstart', function(event) {
                    return
                });

            } else if (isAndroid) {
                window.location.href = 'http://app.myhbp.org.cn/android/%E5%93%88%E4%BD%9B%E7%AE%A1%E7%90%86%E5%AF%BC%E5%B8%88.apk'
                $(".ios-btn ").bind('touchstart', function(event) {
                    return
                });
                $(".android-btn ").bind('touchstart', function(event) {
                    window.location.href = 'http://app.myhbp.org.cn/android/%E5%93%88%E4%BD%9B%E7%AE%A1%E7%90%86%E5%AF%BC%E5%B8%88.apk'
                });
            }
        }
    }


});
```



