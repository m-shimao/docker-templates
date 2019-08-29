From python:3.7

ENV DEBIAN_FRONTEND=noninteractive

RUN pip3 install --upgrade pip && pip install -U Flask

WORKDIR /var/wwww/flask

ENV FLASK_APP=/var/wwww/flask/app.py
