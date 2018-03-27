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

## 4.1 查找nginx目录 {#5-关闭nginx}

```
mac：desktop下command+上方向键 看到user后 shift+command+。 查看隐藏文件usr/local/var/www
```

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

## 8. 配置 nginx.conf {#补充}

路径：usr/local/etc/nginx/nginx.conf

配置：

```
#user  nobody;
worker_processes  1;

#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#pid        logs/nginx.pid;


events {
    worker_connections  1024;
}


http {
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;
    upstream linuxidc {
      server 10.0.6.108:7080;
      server 10.0.0.85:8980;
    }
    server {
        listen       8080;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;

         location / {
             try_files $uri $uri/ @router;
             index index.html;
         }
 
        if (!-e $request_filename) {
            rewrite ^/(.*)  /index.html last;
        }
       # location @router {
       #     rewrite ^.*$ /index.html last;
       #}
        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

        # proxy the PHP scripts to Apache listening on 127.0.0.1:80
        #
        #location ~ \.php$ {
        #    proxy_pass   http://127.0.0.1;
        #}

        # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
        #
        #location ~ \.php$ {
        #    root           html;
        #    fastcgi_pass   127.0.0.1:9000;
        #    fastcgi_index  index.php;
        #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
        #    include        fastcgi_params;
        #}

        # deny access to .htaccess files, if Apache's document root
        # concurs with nginx's one
        #
        #location ~ /\.ht {
        #    deny  all;
        #}
    }


    # another virtual host using mix of IP-, name-, and port-based configuration
    #
    #server {
    #    listen       8000;
    #    listen       somename:8080;
    #    server_name  somename  alias  another.alias;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}


    # HTTPS server
    #
    #server {
    #    listen       443 ssl;
    #    server_name  localhost;

    #    ssl_certificate      cert.pem;
    #    ssl_certificate_key  cert.key;

    #    ssl_session_cache    shared:SSL:1m;
    #    ssl_session_timeout  5m;

    #    ssl_ciphers  HIGH:!aNULL:!MD5;
    #    ssl_prefer_server_ciphers  on;

    #    location / {
    #        root   html;
    #        index  index.html index.htm;
    #    }
    #}
    include servers/*;
}
```

说明： 路由表中mode 用base

## 补充 {#补充}

安装 homebrew ，将以上命令粘贴至terminal，然后回车即可

```
 /usr/bin/ruby -e"$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

参考地址：

[https://brew.sh/index\_zh-cn.html](https://brew.sh/index_zh-cn.html)

[http://www.jianshu.com/p/a23381cdb8b2](http://www.jianshu.com/p/a23381cdb8b2)

