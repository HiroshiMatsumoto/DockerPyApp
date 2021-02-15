# Python App on Docker + Nginx + uWsgi + Flask

The following instructions show building/running python-app on each
Flask, uWsgi, Nginx, Docker servers.

## Flask

simple flask execution by following command

```
python infra/app/app.py
```

with curl command to test

```
curl http://127.0.0.1:5000/
```

it should return "test"

## uWSGI

### configured by command options

```
uwsgi --wsgi-file infra/app/app.py --callable app --http 127.0.0.1:8080
```

```
curl 127.0.0.1:8080/
```

### given configuration file

You need to uncomment `http`, instead socket should be commented-out.

```
http = 127.0.0.1:3031
``` 

```
# socket = :3031
```

then run it by the following command

```
uwsgi --ini infra/app/uwsgi.ini
```

```
curl 127.0.0.1:8080/
```

## nginx

have uwsgi up and running beforehand

```
uwsgi --ini infra/app/uwsgi.ini
```


with the following command

```
mkdir -p var/{log/nginx,run}
```

have local var directory structured like the following

```
var
├── log
│   └── nginx
└── run
```

have the nginx-server up and running using local configuration

```
nginx -p $PWD -c infra/nginx/default.conf
```

```
curl 127.0.0.1:8080/
```


kill the nginx-server process by kill command

```
kill $(cat var/run/nginx.pid)
```

## docker



## Reference
- https://www.python.ambitious-engineer.com/archives/1959#uWSGI
- https://www.python.org/dev/peps/pep-0333/
