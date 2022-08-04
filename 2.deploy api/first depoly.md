## setting up the api first

```cmd
sudo yum update
```

**install python**

```cmd
sudo yum install python3
```

**check the python version**

```
python3 --version
```


**download your repo**
```
git clone repo-url
```

**install the api requirments**
```
sudo pip3 install -r requirments.txt 
```

to check if everything works

**run the api**

if you're using unicorn you can run the command like so

the path may be different depending on the machine
```
sudo /usr/local/bin/uvicorn main:app --reload --port 8000 --host 0.0.0.0 &
```

**now we are using gunicorn to run the api without taking the terminal**

-w stands for no. of workers or instances to run the program

then the program path
```
sudo /usr/local/bin/gunicorn -w 4 -k /usr/local/bin/uvicorn.workers.UvicornWorker main:app --reload --port 8000 --host 0.0.0.0 &
```
