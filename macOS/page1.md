# mac OS 下使用Nginx实现80端口转发8080端口

mac OS 上安装 Nginx 后，默认连接服务器是 **8080** 端口，这里我们修改成 **80** 端口来转发 **8080**端口

- 命令行

```bash
sudo vim /usr/local/etc/nginx/nginx.conf
```

```json
server {
            listen       80;
            server_name  localhost;
    
            #charset koi8-r;
    
            #access_log  logs/host.access.log  main;
    
            location / {
                root   /Users/admin/Desktop/downloads; // 文件目录路径
                access_log on;
                autoindex on;
                proxy_pass http://127.0.0.1:8080;
            }
```

将 **Listen** 改为 **80**  

location 内添加  **proxy_pass http://127.0.0.1:8080;**