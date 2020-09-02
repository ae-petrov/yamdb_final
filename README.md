# Проект: запуск контейнеров на сервере
![Tested and buided](https://github.com/ae-petrov/yamdb_final/workflows/YamDB-appworkflow/badge.svg)

Проект включает в себя корпорацию контейнеров docker-compose (db, web, nginx). Api сервис YamDB и база данных postgres. Статика раздается через Nginx

## Перед использованием

Прочтите инструкции ниже, чтобы установить и запустить докер-контейнеры.

### Предусловия

Установлен docker

### Установка

Клонируйте репозиторий

```
git clone https://github.com/ae-petrov/yamdb_final.git
```

В директории проекта создайте файл .env, в котором пропишит переменные окружения. Используйте .env.example в качестве шаблона.


С помощью Dockerfile и docker-compose.yaml разверните проект
```
docker-compose up --build
```

В новом окне терминала узнайте id контейнера yamdb_final_web и войдите в контейнер
```
docker container ls
```
```
docker exec -it <CONTAINER_ID> bash
```

В контейнере выполните миграции, соберите статику, создайте суперпользователя и заполните базу начальными данными
```
python manage.py migrate

python manage.py collectstatic

python manage.py createsuperuser

python manage.py loaddata fixtures.json
```