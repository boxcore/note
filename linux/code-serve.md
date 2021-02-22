# CodeServe

code-server是vscode的web实现

## 安装
```bash
# 新版的安装方法
curl -fsSL https://code-server.dev/install.sh | sh
```

## 配置

### 添加codeserver自启动服务

```bash
## 旧方法的自启动
cat > /usr/local/bin/codeserver.sh <<EOF
#!/bin/bash
export PASSWORD='YOUR PASS'
/usr/local/bin/code-server --host=127.0.0.1 --port=1024 /root/workspace
EOF

touch /etc/supervisor.d/codeserver.ini
cat > <<"EOF"
[program:codeserver]
autorestart=True
autostart=True
redirect_stderr=True
command="/usr/local/bin/codeserver.sh"
user=root
directory=/root
stdout_logfile=/tmp/codeserver.log
stderr_logfile=/tmp/codeserver.err
EOF



## 新版的自启动




## 添加nginx服务配置
### 独立文件配置
#### 注意要在/www/server/nginx/conf/nginx.conf配置文件  include /www/server/panel/vhost/nginx/*.conf; 前导入配置
include code-server.conf;

cat > /www/server/nginx/conf/code-server.conf <<"EOF"
    server
    {
        listen 2096 ssl http2;
        # listen 2095; # http模式端口
        server_name code-server;
        index index.html index.htm index.php;

        ## ssl start
        ssl_certificate    /www/server/panel/ssl/certificate.pem;
        ssl_certificate_key    /www/server/panel/ssl/privateKey.pem;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2 TLSv1.3;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:HIGH:!aNULL:!MD5:!RC4:!DHE;
        ssl_prefer_server_ciphers on;
        ssl_session_cache shared:SSL:10m;
        ssl_session_timeout 10m;
        ## ssl end

        ##Cloudflare-START
        include cf.conf;
        ##Cloudflare-END

        location / {
		    allow xxx.xxx.xxx.xx;
            deny all;

            proxy_pass http://127.0.0.1:1024;
            # Set WebSocket Proxy
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection upgrade;
        }

        access_log  /www/wwwlogs/code-server.log;
    }
EOF


```