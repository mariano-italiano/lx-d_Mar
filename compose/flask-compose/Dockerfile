FROM python:3.10-alpine

WORKDIR /flask-app

COPY . /flask-app

RUN pip install -r requirements.txt --no-cache-dir

CMD ["python3", "app.py"]
