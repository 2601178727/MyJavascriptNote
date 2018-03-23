## 1. 安装（可以用 brew 安装） {#1-安装可以用-brew-安装}

```
sudo brew install nginx
```

## 2. 查看 nginx 版本 {#2-查看-nginx-版本}

```
 nginx -v
```

## 3. 启动 nginx {#3-启动-nginx}

```
sudo nginx  
```

也可以使用下面的命令启动，但是配置文件nginx.conf修改后用这个命令执行不生效，故不建议使用：

```
sudo brew services start nginx
```

## 4. 查看 nginx 是否启动成功 {#4-查看-nginx-是否启动成功}

在浏览器中访问[http://localhost:8080](http://localhost:8080/)，如果出现如下界面，则说明启动成功.

![](http://img.blog.csdn.net/20170526212421812?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvemp1d3dq/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast "这里写图片描述")

备注：端口号是在配置文件nginx.conf里面配置的，默认端口是8080，配置文件的位置/usr/local/etc/nginx

## 5. 关闭nginx {#5-关闭nginx}

```
sudo nginx -s stop
```

也可以使用下面的命令启动，但是配置文件nginx.conf修改后用这个命令执行不生效，故不建议使用：

```
sudo brew services stop nginx
```

## 6. 重新加载nginx {#6-重新加载nginx}

```
sudo nginx -s reload
```

## 7. 可能遇到的问题 {#7-可能遇到的问题}

* 端口被占用

  > nginx: \[emerg\] bind\(\) to 0.0.0.0:80 failed \(48: Address already in use\)

  解决方法：修改 nginx.conf 文件里的端口号

* 权限不够

  > nginx: \[alert\] could not open error log file: open\(\) “/usr/local/var/log/nginx/error.log” failed \(13: Permission denied\)

  解决方法：在命令前加上 sudo，这时可能会要求输入密码，密码就是电脑的开机密码啦~

## 补充 {#补充}

安装 homebrew ，将以上命令粘贴至terminal，然后回车即可

```
 /usr/bin/ruby -e"$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

参考地址：

[https://brew.sh/index\_zh-cn.html](https://brew.sh/index_zh-cn.html)

[http://www.jianshu.com/p/a23381cdb8b2](http://www.jianshu.com/p/a23381cdb8b2)

