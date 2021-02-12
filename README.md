# Python App on Docker + Nginx + uWsgi + Flask

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

```
uwsgi --ini infra/app/uwsgi.ini
```

```
curl 127.0.0.1:8080/
```

## Reference
- https://www.python.ambitious-engineer.com/archives/1959#uWSGI
- https://www.python.org/dev/peps/pep-0333/
