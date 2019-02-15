### 在Linux上部署Asp.net Core应用

* self-contained方式部署<br/>
asp.net core应用发布时使用命令：dotnet publish --framework netcoreapp2.1 --runtime ubuntu.18.04-x64 -c release --self-contained true<br/>
其中RID为运行时标识符，如linux-x64、ubuntu.14.04-x64等。

* 安装Nginx <br/>
sudo apt-get update <br/>
sudo apt-get install nginx <br/>

* 配置Nginx
修改/etc/nginx/sites-available/default文件：
```javascript
server {
    listen        80;
    server_name   example.com *.example.com;
    location / {
        proxy_pass         http://localhost:5000;
        proxy_http_version 1.1;
        proxy_set_header   Upgrade $http_upgrade;
        proxy_set_header   Connection keep-alive;
        proxy_set_header   Host $host;
        proxy_cache_bypass $http_upgrade;
        proxy_set_header   X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header   X-Forwarded-Proto $scheme;
    }
}
```
* 启动Nginx <br/>
sudo systemctl restart nginx


* 启动Asp.net Core应用 <br/>
sudo ./Webapp
