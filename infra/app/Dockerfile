FROM python:3.7.9

WORKDIR /usr/src/app

COPY requirements.txt .

RUN pip install -r requirements.txt

# COPY uwsgi.ini .
# COPY app.py .

# CMD 命令は、イメージが起動されたときに実行するコマンドを指定します。
CMD ["uwsgi","--ini","/usr/src/app/uwsgi.ini"]
# CMD ["ls","/usr/src/app"]
