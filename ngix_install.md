https://huudoanh.com/huong-dan-cai-dat-nginx-tren-centos-8/


sudo mkdir -p /var/www/tungngix/html

sudo chown -R $USER:$USER /var/www/tungngix/html

vi /var/www/tungngix/html/index.html


```
<html>
    <head>
        <title>Welcome to tungngix</title>
    </head>
    <body>
        <h1>Success! Your Nginx server is successfully configured for <em>tungngix</em>. </h1>
<p>This is a sample page.</p>
    </body>
</html>
```

sudo vi /etc/nginx/conf.d/tungngix.conf

```
server {
        listen 80;
        listen [::]:80;

        root /var/www/tungngix/html;
        index index.html index.htm index.nginx-debian.html;

        server_name tungngix www.tungngix;

        location / {
                try_files $uri $uri/ =404;
        }
}
```

sudo nginx -t

sudo systemctl restart nginx

chcon -vR system_u:object_r:httpd_sys_content_t:s0 /var/www/tungngix/
