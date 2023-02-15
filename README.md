# yamdb_final ![YAMDB_FINAL Status](https://github.com/elenashovtyuk/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg)

## Описание

Проект YaMDb собирает отзывы (Review) пользователей на произведения (Title).
Произведения делятся на категории: "Книги", "Фильмы", "Музыка". Список категорий (Category) может быть расширен.
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка.
Новые жанры может создавать только администратор.
Пользователи оставляют к произведениям текстовые отзывы (Review) и выставляют произведению рейтинг,
а также пишут комментарии (Comments) к отзывам.

## Используемые технологии

- Python 3.7
- Django 2.2.16
- Django Rest Framework 3.12.4
- Gunicorn 20.0.4
- Nginx 1.21.3-alpine
- Postres 13.0-alpine
- Docker 20.10.23
- Docker Compose 2.15.1
- Postman (графическая программа для тестирования API)


## Запуск проекта

### Клонируем проект

Клонировать репозиторий и перейти в него в командной строке:

git clone git@github.com:elenashovtyuk/infra-sp2.git

### Cоздаем и активируем виртуальное окружение

Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

```
source venv/bin/activate
```

### Установим зависимости

```
python3 -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

### Переходим в папку с файлом docker-compose.yaml

```
cd infra
```
### Запустим проект в контейнерах, находясь в директории с docker-compose.yaml

```
docker-compose up -d --build
```

### Выполним миграции

```
docker compose exec web python manage.py makemigrations reviews
```

### Создаем суперпользователя

```
docker compose exec web python manage.py createsuperuser
```

### Собираем все статические файлы в папку static

```
docker compose exec web python manage.py collectstatic --no-input
```

### Создаем дамп (резервную копию) базы данных

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

### Приложение активно и готово к использованию

Можно перейти по адресу http://localhost/admin/ и авторизоваться (ввести свои данные от созданного суперпользователя).


## Документация API Yamdb

Доступна после запуска сервера: http://localhost/redoc/


## Авторы проекта
Шовтюк Елена, Михайлова Мария, Пиголкин Андрей
