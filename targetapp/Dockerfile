FROM python:3.8

WORKDIR /

ENV FLASK_APP=app.py
ENV FLASK_RUN_HOST=0.0.0.0

COPY app.py ./
COPY requirements.txt ./

RUN pip install --upgrade pip
RUN pip install -r requirements.txt

ENTRYPOINT [ "flask", "run" ]