![example workflow](https://github.com/denisgrinch/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# api_yamdb
### Описание
Блог для тех кто хочет высказать свое мнение, но через api.
ресурс доступен по адресу http://51.250.30.174 
### Технологии
- Python 3.7
- Django 2.2.16
- Djangorestframework 3.12.4
- Docker 20.10.17
- Nginx 1.21.3

### Запуск проекта
- Запустите контейнеры командой docker-compose up

- Создайте суперпользователя:
    docker-compose run web python manage.py createsuperuser
- имортируйте данные из дампа:
    docker-compose run web python manage.py loaddata fixtures.json

### Шаблон настройки переменных окружения
- основные параметры для запуска проекта
    SECRET_KEY=<секретный ключ> 
    DEBUG=<режим отладки True или False>
    ALLOWED_HOSTS=<список хостов имеющих доступ к ресурсу>

- параметры для подключения БД

    ENGINE='django.db.backends.postgresql'
    NAME='postgres'
    USER=<имя пользователя БД>
    PASSWORD=<пароль для подключения к БД>
    HOST=<имя хоста на котором развёрнута БД>
    PORT=<порт подключения к БД. поумолчанию '5432'>

### Примеры запросов
- POST /api/v1/auth/token/
```json
{
  "username": "string",
  "confirmation_code": "string"
}
```
> <font color="blue">200</font>
```json
{
  "token": "string"
}
```
- GET api/v1/titles/
> <font color="green">200</font>
```json
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "name": "string",
        "year": 0,
        "rating": 0,
        "description": "string",
        "genre": [
          {
            "name": "string",
            "slug": "string"
          }
        ],
        "category": {
          "name": "string",
          "slug": "string"
        }
      }
    ]
  }
]
```
- POST api/v1/titles/{title_id}/reviews/
```json
{
  "text": "string",
  "score": 1
}
```
> <font color="blue">201</font>
```json
{
  "id": 0,
  "text": "string",
  "author": "string",
  "score": 1,
  "pub_date": "2019-08-24T14:15:22Z"
}
```
### Авторы
Умар Ширваниев
Денис Карпушин
Бакакин Павел