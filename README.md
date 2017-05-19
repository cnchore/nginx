# 知识要点

## 1.安装
`brew install nginx`

## 2.配置
打开/usr/local/etc/nginx/nginx.conf （配置文件路径）
根据项目需求，自行配置，参数说明如下：

```
server {

        listen       6688;//端口
        server_name  localhost;//域名
        underscores_in_headers  on;#cookie允许有下划线
        location /admin/{
              proxy_set_header Host $host;//代理主机

              proxy_set_header X-Real-IP $remote_addr;#真实ip

              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

              proxy_set_header Cookie $http_cookie;

              proxy_pass 要代理的地址;

              proxy_cookie_domain 目标domain nginx;

              proxy_redirect off;

              proxy_cookie_path /admin/ /admin/;#cookie生成路径
        }
}
```
## 3.启动方法：

启动：`nginx`

停止：`nginx -s stop`

重载：`nginx reload`
