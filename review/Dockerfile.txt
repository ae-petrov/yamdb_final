# создать образ на основе базового сло€ python (там будет ќ— и интерпретатор Python)
FROM python:3.8

# выбрать или создать директорию /code
WORKDIR /code

# скопировать всЄ содержимое директории, в которой лежит докерфайл, в директорию /code
COPY . /code

RUN mkdir staticfiles

# выполнить команду (как в терминале, с тем же синтаксисом) дл€ установки пакетов из requirements.txt
RUN pip install -r /code/requirements.txt

CMD gunicorn api_yamdb.wsgi:application --bind 0.0.0.0:8000
