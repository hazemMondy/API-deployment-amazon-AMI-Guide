## 1. now to make the api starts automatically
```cmd
cd /etc/systemd/system
sudo nano api.service

```

exdcstart is the command whatever runs your app
, workers and path depends on yout project


> this is how the api.service file should look like
```json
[Unit]
Descripion= My API Application
After=network.target

[Service]
User=ec2-user
Group=ec2-user

ExecStart= sudo /usr/local/bin/gunicorn -w 1 -k uvicorn.workers.UvicornWorker 
main:app --bind 0.0.0.0:8000

[Install]
WantedBy=multi-user.target

```

## 2. now start the api
```cmd
sudo systemctl start api.service
sudo systemctl status api.service
sudo systemctl daemon-reload
```

**check the status**
```cmd
sudo systemctl status api.service
```
**if you changed any code from api run the following command**
```cmd
sudo systemctl daemon-reload
```

## 3. to make it auto atart after reboot of the server
```cmd
sudo systemctl enable api.service
```