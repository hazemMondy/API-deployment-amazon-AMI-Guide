## 1. install nginx
```cmd
sudo amazon-linux-extras install nginx1 -y
```
<!-- sudo yml install nginx -y -->

<!-- sudo yum update -->
## 2. setup nginx

**go to this dir**
```
sudo nano /etc/nginx/nginx.conf
```
**remember to stop the api.service to be able to check nginx**
```
sudo systemctl stop api.service
```

  <!-- 228  cd /etc/nginx/sites-available/
  229  ls
  230  vim nginx.conf  -->
  <!-- sudo nano /etc/nginx/nginx.conf -->
*the file should contain alot of code ,but we're concerned about those*
```
include /etc/nginx/conf.d/*.conf;

server {
    listen       80;
    listen       [::]:80;
    server_name  _;
    root         /usr/share/nginx/html;

    # Load configuration files for the default server block.
    include /etc/nginx/default.d/*.conf;
    location / {
            proxy_pass http://localhost:8000;}
    error_page 404 /404.html;
    location = /404.html {
    }

    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
    }
}
```
**where**
server_name: if you have domain name else leave it as it is

**imp** under the include set the proxy to the api port

  location / {
    proxy_pass http://localhost:8000;
    }

**now start the nginx service**
```
sudo service nginx start
```


## 3. to make it auto atart after reboot of the server

```
sudo systemctl enable nginx
```